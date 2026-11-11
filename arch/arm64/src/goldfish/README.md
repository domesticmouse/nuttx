# goldfish (`nuttx/arch/arm64/src/goldfish`)

## Overview
Hardware abstraction and architecture package for `goldfish` under `nuttx/arch/arm64/src/goldfish`, providing 3 header file(s) and 3 source file(s) (including `chip.h`, `goldfish_boot.h`, `goldfish_serial.h`, `goldfish_boot.c`).

## Interface
- `[goldfish_boot.h:goldfish_board_initialize]`
- `[goldfish_boot.h:CONFIG_SYS_CLOCK_HW_CYCLES_PER_SEC]`
- `[goldfish_boot.h:GOLDFISH_PMU_CYCLES_PER_SEC]`
- `[goldfish_serial.h:CONFIG_QEMU_UART_BASE]`
- `[goldfish_serial.h:CONFIG_QEMU_UART_IRQ]`
- `[goldfish_boot.c:arm64_get_mpid]`
- `[goldfish_boot.c:arm64_get_cpuid]`
- `[goldfish_boot.c:arm64_el_init]`
- `[goldfish_boot.c:arm64_chip_boot]`
- `[goldfish_boot.c:arm64_netinitialize]`
- `[goldfish_rtc.c:up_rtc_initialize]`
- `[goldfish_serial.c:arm64_earlyserialinit]`
- `[goldfish_serial.c:arm64_serialinit]`
- `[CMakeLists.txt:target_sources]`
- `[Kconfig:CONFIG_GOLDFISH_RTC_PL031_BASE]`
- `[Kconfig:CONFIG_GOLDFISH_RTC_PL031_IRQ]`
- `[Make.defs:CHIP_CSRCS]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
