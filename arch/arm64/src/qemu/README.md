# qemu (`nuttx/arch/arm64/src/qemu`)

## Overview
Hardware abstraction and architecture package for `qemu` (Qemu Virt Chip Selection) under `nuttx/arch/arm64/src/qemu`, providing 3 header file(s) and 5 source file(s) (including `chip.h`, `qemu_boot.h`, `qemu_serial.h`, `qemu_boot.c`).

## Interface
- `[qemu_boot.h:qemu_board_initialize]`
- `[qemu_boot.h:CONFIG_SYS_CLOCK_HW_CYCLES_PER_SEC]`
- `[qemu_serial.h:CONFIG_QEMU_UART_BASE]`
- `[qemu_serial.h:CONFIG_QEMU_UART_IRQ]`
- `[qemu_boot.c:arm64_get_mpid]`
- `[qemu_boot.c:arm64_get_cpuid]`
- `[qemu_boot.c:arm64_el_init]`
- `[qemu_boot.c:arm64_chip_boot]`
- `[qemu_initialize.c:arm64_pminitialize]`
- `[qemu_initialize.c:up_idle]`
- `[qemu_rtc.c:up_rtc_initialize]`
- `[qemu_serial.c:arm64_earlyserialinit]`
- `[qemu_serial.c:arm64_serialinit]`
- `[qemu_textheap.c:up_textheap_memalign]`
- `[qemu_textheap.c:up_textheap_free]`
- `[qemu_textheap.c:up_textheap_heapmember]`
- `[CMakeLists.txt:target_sources]`
- `[Kconfig:CONFIG_ARCH_CHIP_QEMU_A53]`
- `[Kconfig:CONFIG_ARCH_CHIP_QEMU_A57]`
- `[Kconfig:CONFIG_ARCH_CHIP_QEMU_A72]`
- `[Kconfig:CONFIG_ARCH_CHIP_QEMU_UNKNOWN]`
- `[Kconfig:CONFIG_ARCH_CHIP_QEMU_WITH_HV]`
- `[Kconfig:CONFIG_QEMU_RTC_PL031_BASE]`
- `[Kconfig:CONFIG_QEMU_RTC_PL031_IRQ]`
- `[Kconfig:CONFIG_QEMU_RTC_PL031_SYNC]`
- `[Make.defs:CHIP_CSRCS]`

## Invariants
- None

## Side Effects
- `[qemu_rtc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)

## Verification
- Run: `make test`
