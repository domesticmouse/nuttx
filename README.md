<p align="center">
<img src="https://raw.githubusercontent.com/apache/nuttx/master/Documentation/_static/NuttX320.png" width="175">
</p>

![POSIX Badge](https://img.shields.io/badge/POSIX-Compliant-brightgreen?style=flat&label=POSIX)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue)](https://nuttx.apache.org/docs/latest/introduction/licensing.html)
![Issues Tracking Badge](https://img.shields.io/badge/issue_track-github-blue?style=flat&label=Issue%20Tracking)
[![Contributors](https://img.shields.io/github/contributors/apache/nuttx)](https://github.com/apache/nuttx/graphs/contributors)
[![GitHub Build Badge](https://github.com/apache/nuttx/workflows/Build/badge.svg)](https://github.com/apache/nuttx/actions/workflows/build.yml)
[![Documentation Badge](https://github.com/apache/nuttx/workflows/Build%20Documentation/badge.svg)](https://nuttx.apache.org/docs/latest/index.html)
[![MemBrowse](https://membrowse.com/badge.svg)](https://membrowse.com/public/apache/nuttx)

Apache NuttX is a real-time operating system (RTOS) with an emphasis on
standards compliance and small footprint. Scalable from 8-bit to 64-bit
microcontroller environments, the primary governing standards in NuttX are POSIX
and ANSI standards. Additional standard APIs from Unix and other common RTOSs
(such as VxWorks) are adopted for functionality not available under these
standards, or for functionality that is not appropriate for deeply-embedded
environments (such as fork()).

For brevity, many parts of the documentation will refer to Apache NuttX as simply NuttX.

## Getting Started
First time on NuttX? Read the [Getting Started](https://nuttx.apache.org/docs/latest/quickstart/index.html) guide!
If you don't have a board available, NuttX has its own simulator that you can run on terminal. For first-time contributors, building the simulator locally is a useful way to verify the development environment before submitting changes.

## Documentation
You can find the current NuttX documentation on the [Documentation Page](https://nuttx.apache.org/docs/latest/).

Alternatively, you can build the documentation yourself by following the Documentation Build [Instructions](https://nuttx.apache.org/docs/latest/contributing/documentation.html).

The old NuttX documentation is still available in the [Apache wiki](https://cwiki.apache.org/NUTTX/NuttX).

## Supported Boards
NuttX supports a wide variety of platforms. See the full list on the [Supported Platforms](https://nuttx.apache.org/docs/latest/platforms/index.html) page.

## Contributing
If you wish to contribute to the NuttX project, read the [Contributing](https://nuttx.apache.org/docs/latest/contributing/index.html) guidelines for information on Git usage, coding standard, workflow and the NuttX principles.

## License
The code in this repository is under either the Apache 2 license, or a license compatible with the Apache 2 license. See the [License Page](https://nuttx.apache.org/docs/latest/introduction/licensing.html) for more information.

## Overview

The `nuttx` directory contains the Apache NuttX Real-Time Operating System (RTOS) kernel, standard libraries, hardware abstraction layers, board support packages, device drivers, filesystems, and networking stacks. It is organized into processor architectures (`arch`), board support packages (`boards`), the task scheduler and OS core (`sched`), memory management (`mm`), virtual and storage filesystems (`fs`), the kernel networking stack (`net`), upper/lower-half device drivers (`drivers`), standard C/C++/math/DSP/graphics libraries (`libs`), public POSIX and kernel headers (`include`), system call tables (`syscall`), binary format loaders (`binfmt`), cryptographic services (`crypto`), audio/video/graphics/wireless frameworks (`audio`, `video`, `graphics`, `wireless`), Sphinx documentation (`Documentation`), and host build/configuration tools (`tools`).

## Subdirectories & Boundaries

- `Documentation`: [./Documentation/README.md](./Documentation/README.md) - Sphinx documentation configuration (`conf.py`), URL redirect mappings (`redirects.py`), and custom Sphinx build extensions (`_extensions`).
- `arch`: [./arch/README.md](./arch/README.md) - Architecture-specific Hardware Abstraction Layer (HAL) across 18 CPU architectures (`arm`, `arm64`, `avr`, `ceva`, `hc`, `mips`, `misoc`, `or1k`, `renesas`, `risc-v`, `sim`, `sparc`, `tricore`, `x86`, `x86_64`, `xtensa`, `z16`, `z80`).
- `audio`: [./audio/README.md](./audio/README.md) - Upper-half audio character driver (`audio.c`), composite audio device wrapper (`audio_comp.c`), and WAV/PCM stream decoder (`pcm_decode.c`).
- `binfmt`: [./binfmt/README.md](./binfmt/README.md) - Binary format loader subsystem managing registration and execution of builtin, `#!` script, ELF, and NXFLAT (`libnxflat`) binaries.
- `boards`: [./boards/README.md](./boards/README.md) - Top-level board support subsystem implementing `boardctl()` (`boardctl.c`) and Board Support Packages (BSPs) across 17 target CPU architectures.
- `crypto`: [./crypto/README.md](./crypto/README.md) - OpenBSD-derived cryptographic framework (`crypto.c`), `/dev/crypto` character device (`cryptodev.c`), software cryptographic driver (`cryptosoft.c`), cipher/hash algorithms, and CSPRNG entropy pool (`random_pool.c`).
- `drivers`: [./drivers/README.md](./drivers/README.md) - Upper-half and generic device drivers across 57 driver subsystems (`1wire`, `aie`, `analog`, `audio`, `bch`, `can`, `clk`, `contactless`, `coresight`, `crypto`, `devfreq`, `devicetree`, `dma-buf`, `eeprom`, `efuse`, `i2c`, `i2s`, `i3c`, `input`, `ioexpander`, `ipcc`, `lcd`, `leds`, `loop`, `math`, `misc`, `mmcsd`, `modem`, `motor`, `mtd`, `net`, `note`, `pci`, `pinctrl`, `pipes`, `power`, `rc`, `regmap`, `reset`, `rf`, `rpmsg`, `rptun`, `segger`, `sensors`, `serial`, `spi`, `syslog`, `thermal`, `timers`, `usbdev`, `usbhost`, `usbmisc`, `usbmonitor`, `usrsock`, `vhost`, `video`, `virtio`, `wireless`).
- `fs`: [./fs/README.md](./fs/README.md) - Virtual File System (VFS) core, inode tree, dedicated filesystem heap (`fs_heap`), POSIX IPC pseudo-filesystems (`mqueue`, `semaphore`, `shm`, `event`), and storage/network filesystems (`aio`, `binfs`, `cromfs`, `driver`, `fat`, `hostfs`, `littlefs`, `mmap`, `mnemofs`, `mount`, `nfs`, `nxffs`, `partition`, `procfs`, `romfs`, `rpmsgfs`, `smartfs`, `socket`, `spiffs`, `tmpfs`, `unionfs`, `userfs`, `v9fs`, `vfs`, `xipfs`, `zipfs`).
- `graphics`: [./graphics/README.md](./graphics/README.md) - NuttX Graphics (`NX`) windowing and rasterization subsystem (`nxbe`, `nxglib`, `nxmu`, `nxterm`).
- `include`: [./include/README.md](./include/README.md) - Standard C, POSIX, BSD/GNU compatibility headers (`arpa`, `cxx`, `net`, `netinet`, `netpacket`, `ssp`, `sys`) and internal kernel/driver headers (`nuttx`).
- `libs`: [./libs/README.md](./libs/README.md) - Standard C library (`libc`), math library (`libm`), C++ runtime support (`libxx`), compiler builtins (`libbuiltin`), DSP library (`libdsp`), and NX client graphics library (`libnx`).
- `mm`: [./mm/README.md](./mm/README.md) - Memory management subsystem including kernel/user heaps (`mm_heap`, `umm_heap`, `kmm_heap`), TLSF allocator (`tlsf`), memory pools (`mempool`), granule allocator (`mm_gran`), I/O buffers (`iob`), memory mapping (`map`, `kmap`, `shm`), and sanitizers (`kasan`, `ubsan`).
- `net`: [./net/README.md](./net/README.md) - Kernel networking stack providing BSD/POSIX sockets (`socket`), network device abstraction (`netdev`, `devif`), and protocol families (`arp`, `bluetooth`, `can`, `icmp`, `icmpv6`, `ieee802154`, `igmp`, `inet`, `ipfilter`, `ipfrag`, `local`, `mld`, `nat`, `neighbor`, `netfilter`, `netforward`, `netlink`, `netpoll`, `pkt`, `procfs`, `route`, `rpmsg`, `sixlowpan`, `tcp`, `udp`, `usrsock`, `utils`).
- `sched`: [./sched/README.md](./sched/README.md) - Kernel bootstrap (`init`), task scheduler (`sched`), task/thread lifecycle (`task`, `pthread`, `group`, `tls`), IPC and synchronization (`semaphore`, `event`, `signal`, `mqueue`), timers/clocks (`clock`, `wdog`, `timer`, `hrtimer`), interrupt dispatch (`irq`), work queues (`wqueue`), address environments (`addrenv`, `paging`), loadable modules (`module`), and instrumentation (`instrument`, `misc`).
- `syscall`: [./syscall/README.md](./syscall/README.md) - System call table (`syscall.csv`), syscall name lookup array (`g_funcnames`), and kernel syscall stub lookup table (`g_stublookup`).
- `tools`: [./tools/README.md](./tools/README.md) - Host configuration utilities (`configure.sh`, `configure.c`, `mkconfig.c`), build generators (`mksyscall.c`, `mksymtab.c`, `mkdeps.c`, `mkversion.c`), code style checker (`nxstyle.c`), GDB scripts (`pynuttx`), and SoC image packaging tools.
- `video`: [./video/README.md](./video/README.md) - Video subsystem build glue and display timing / EDID parser library (`videomode`).
- `wireless`: [./wireless/README.md](./wireless/README.md) - Kernel wireless protocol stacks including Bluetooth Low Energy (`bluetooth`), IEEE 802.15.4 MAC (`ieee802154`), and generic packet radio (`pktradio`).

## Interface

- `[sched/init/nx_start.c:nx_start]` Kernel initialization entry point (`void nx_start(void)`) invoked by architecture startup code to initialize heaps, task lists, VFS, drivers, networking, and the idle/init tasks.
- `[boards/boardctl.c:boardctl]` User/kernel control interface (`int boardctl(unsigned int cmd, uintptr_t arg)`) for board initialization, power management, reset, symbol tables, RAM/ROM disks, USB, and NX servers.
- `[drivers/drivers_initialize.c:drivers_initialize]` Registers and initializes configured kernel character, block, and special device drivers under `/dev`.
- `[fs/fs_initialize.c:fs_initialize]` Initializes the Virtual File System, inode tree, and filesystem heap.
- `[net/net_initialize.c:net_initialize]` Initializes the kernel networking stack, socket descriptors, and protocol pools.
- `[syscall/syscall_stublookup.c:g_stublookup]` Kernel system call dispatch table (`const uintptr_t g_stublookup[SYS_nsyscalls]`) mapping user-space traps to kernel handlers.

## Invariants

- Initialization state (`g_nx_initstate`) progresses monotonically through `OSINIT_BOOT`, `OSINIT_TASKLISTS`, `OSINIT_MEMORY`, `OSINIT_OSREADY`, and `OSINIT_IDLELOOP` during `nx_start()` `[sched/init/nx_start.c:g_nx_initstate]`.
- Architectural rules in `INVIOLABLES.md` require strict separation between portable OS code (`sched`, `fs`, `net`, `mm`, `drivers`) and architecture/board code (`arch`, `boards`), and mandate C89/POSIX compliance across core kernel headers.
- Every system call index up to `SYS_nsyscalls` must match between `[syscall/syscall.csv]`, `[syscall/syscall_names.c:g_funcnames]`, and `[syscall/syscall_stublookup.c:g_stublookup]`.

## Side Effects

- Running `tools/configure.sh <board>:<config>` writes `.config`, `Make.defs`, and `include/nuttx/config.h` in the `nuttx` root directory.
- Kernel execution mutates hardware MMIO registers (`arch/*`, `boards/*`), manages physical/virtual memory pools (`mm/*`), mounts storage filesystems (`fs/*`), and dispatches hardware interrupts and context switches (`sched/*`).

## Verification

- Run: `make test`

