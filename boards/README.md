# NuttX Boards Subsystem (`nuttx/boards`)

## Overview
Top-level board support subsystem for Apache NuttX. Implements the `boardctl()` OS control interface (`boardctl.c`), build archive scaffolding (`dummy.c`, `Board.mk`, `Makefile`, `CMakeLists.txt`), and coordinates board support packages (BSPs) across 17 target CPU architectures.

## Interface
- `[boardctl.c:boardctl]` Public OS interface `int boardctl(unsigned int cmd, uintptr_t arg)` (`CONFIG_BOARDCTL`) handling `BOARDIOC_FINALINIT`, `BOARDIOC_POWEROFF`, `BOARDIOC_RESET`, `BOARDIOC_PM_CONTROL`, `BOARDIOC_UNIQUEID`, `BOARDIOC_UNIQUEKEY`, `BOARDIOC_SWITCH_BOOT`, `BOARDIOC_BOOT_IMAGE`, `BOARDIOC_MKRD`, `BOARDIOC_ROMDISK`, `BOARDIOC_APP_SYMTAB`, `BOARDIOC_OS_SYMTAB`, `BOARDIOC_USBDEV_CONTROL`, `BOARDIOC_NX_START`, `BOARDIOC_VNC_START`, `BOARDIOC_NXTERM`, `BOARDIOC_NXTERM_IOCTL`, `BOARDIOC_SPINLOCK`, `BOARDIOC_RESET_CAUSE`, `BOARDIOC_IRQ_AFFINITY`, `BOARDIOC_START_CPU`, `BOARDIOC_MACADDR`, and fallback `board_ioctl`
- `[dummy.c:__boards_dummy]` Public no-op function `void __boards_dummy(void)` ensuring `libboards` archive is non-empty
- `[Board.mk:libboard]` Build rules for board archive `libboard$(LIBEXT)` and optional ROMFS image source `etctmp.c` (`ETCSRC`) from `RCSRCS` and `RCRAWS`
- `[CMakeLists.txt:board]` CMake kernel library target `board` (`nuttx_add_kernel_library(board)`) adding `boardctl.c` and active board subdirectories
- `[Makefile:libboards]` Make target building `libboards$(LIBEXT)` (`BIN`) from `dummy.c` and `boardctl.c` (`CONFIG_BOARDCTL`)
- `[Kconfig:ARCH_BOARD_*]` Top-level board selection `choice` (default `ARCH_BOARD_CUSTOM`) and `ARCH_BOARD_*` Kconfig definitions
- [`arm`](./arm/README.md): Intermediate blueprint grouping board support packages (BSPs) and SoC/MCU families for the `arm` architecture (83 chip/family subdirectories).
- [`arm64`](./arm64/README.md): Intermediate blueprint grouping board support packages (BSPs) and SoC/MCU families for the `arm64` architecture (11 chip/family subdirectories).
- [`avr`](./avr/README.md): Intermediate blueprint grouping board support packages (BSPs) and SoC/MCU families for the `avr` architecture (4 chip/family subdirectories).
- [`hc`](./hc/README.md): Intermediate blueprint grouping board support packages (BSPs) and SoC/MCU families for the `hc` architecture (1 chip/family subdirectories).
- [`mips`](./mips/README.md): Intermediate blueprint grouping board support packages (BSPs) and SoC/MCU families for the `mips` architecture (3 chip/family subdirectories).
- [`misoc`](./misoc/README.md): Intermediate blueprint grouping board support packages (BSPs) and SoC/MCU families for the `misoc` architecture (1 chip/family subdirectories).
- [`or1k`](./or1k/README.md): Intermediate blueprint grouping board support packages (BSPs) and SoC/MCU families for the `or1k` architecture (1 chip/family subdirectories).
- [`renesas`](./renesas/README.md): Intermediate blueprint grouping board support packages (BSPs) and SoC/MCU families for the `renesas` architecture (3 chip/family subdirectories).
- [`risc-v`](./risc-v/README.md): Intermediate blueprint grouping board support packages (BSPs) and SoC/MCU families for the `risc-v` architecture (26 chip/family subdirectories).
- [`sim`](./sim/README.md): Intermediate blueprint grouping board support packages (BSPs) and SoC/MCU families for the `sim` architecture (1 chip/family subdirectories).
- [`sparc`](./sparc/README.md): Intermediate blueprint grouping board support packages (BSPs) and SoC/MCU families for the `sparc` architecture (3 chip/family subdirectories).
- [`tricore`](./tricore/README.md): Intermediate blueprint grouping board support packages (BSPs) and SoC/MCU families for the `tricore` architecture (2 chip/family subdirectories).
- [`x86`](./x86/README.md): Intermediate blueprint grouping board support packages (BSPs) and SoC/MCU families for the `x86` architecture (1 chip/family subdirectories).
- [`x86_64`](./x86_64/README.md): Intermediate blueprint grouping board support packages (BSPs) and SoC/MCU families for the `x86_64` architecture (1 chip/family subdirectories).
- [`xtensa`](./xtensa/README.md): Intermediate blueprint grouping board support packages (BSPs) and SoC/MCU families for the `xtensa` architecture (3 chip/family subdirectories).
- [`z16`](./z16/README.md): Intermediate blueprint grouping board support packages (BSPs) and SoC/MCU families for the `z16` architecture (1 chip/family subdirectories).
- [`z80`](./z80/README.md): Intermediate blueprint grouping board support packages (BSPs) and SoC/MCU families for the `z80` architecture (4 chip/family subdirectories).

## Invariants
- `[boardctl.c:boardctl]` Requires caller to hold `PR_CAP_ADMIN` capability (`nxsched_capable(PR_CAP_ADMIN)`) for `BOARDIOC_POWEROFF` and `BOARDIOC_RESET`, returning `-EPERM` otherwise
- `[boardctl.c:boardctl]` Enforces `DEBUGASSERT(arg != 0)` for `BOARDIOC_PM_CONTROL`, `BOARDIOC_BOOT_IMAGE`, `BOARDIOC_APP_SYMTAB`, `BOARDIOC_OS_SYMTAB`, `BOARDIOC_USBDEV_CONTROL`, and `BOARDIOC_RESET_CAUSE`
- `[boardctl.c:boardctl_usbdevctrl]` Enforces `DEBUGASSERT(ctrl->handle != NULL)` on `BOARDIOC_USBDEV_CONNECT` and `DEBUGASSERT(ctrl->handle != NULL && *ctrl->handle != NULL)` on `BOARDIOC_USBDEV_DISCONNECT`
- `[boardctl.c:boardctl]` Validates non-null `arg` for `BOARDIOC_MKRD`, `BOARDIOC_ROMDISK`, `BOARDIOC_VNC_START`, and `BOARDIOC_NXTERM`, returning `-EINVAL` if null
- `[boardctl.c:boardctl]` Sets thread `errno` to `-ret` via `set_errno(-ret)` and returns `ERROR` (`-1`) whenever a sub-handler returns `ret < 0`

## Side Effects
- `[boardctl.c:boardctl]` Mutates global OS init state `g_nx_initstate = OSINIT_RESET`, emits `sched_trace_mark("RESET")`, invokes `reboot_notifier_call_chain`, flushes data cache via `up_flush_dcache_all()`, and triggers hardware reset/poweroff on `BOARDIOC_RESET` and `BOARDIOC_POWEROFF`
- `[boardctl.c:boardctl]` Mutates thread `errno` via `set_errno(-ret)` when `ret < 0`
- `[boardctl.c:boardctl]` Mutates application/OS symbol tables (`exec_setsymtab`, `libelf_setsymtab`), PM states (`boardctl_pmctrl`), spinlocks/IRQs (`BOARDIOC_SPINLOCK`, `up_affinity_irq`), SMP CPU cores (`board_start_cpu`), RAM/ROM disks (`mkrd`, `romdisk_register`), USB device states (`boardctl_usbdevctrl`), and NX/VNC graphics servers (`nxmu_start`, `nx_vnc_fbinitialize`, `nx_register`, `nxtk_register`, `nxtool_register`, `nxterm_ioctl_tap`)
- `[Board.mk:ETCSRC]` Creates temporary directory `etctmp`, runs `board_romfs_mkpasswd.sh`, builds `romfs.img` via `genromfs`, generates `etctmp.c` via `xxd`, and removes `romfs.img`
- `[CMakeLists.txt:board]` Generates `${NUTTX_BINARY_DIR}/dummy.c` and symlinks `${NUTTX_BINARY_DIR}/arch/${CONFIG_ARCH}/src/board/board` to `${NUTTX_BOARD_ABS_DIR}/src`

## Verification
- Run: `./tools/configure.sh sim:nsh && make`
