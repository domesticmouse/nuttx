# fvp-v8r-aarch32 (`nuttx/arch/arm/src/fvp-v8r-aarch32`)

## Overview
Hardware abstraction and architecture package for `fvp-v8r-aarch32` (FVP ARMv8-R Virt Chip Selection) under `nuttx/arch/arm/src/fvp-v8r-aarch32`, providing 2 header file(s) and 2 source file(s) (including `chip.h`, `fvp_boot.h`, `fvp_boot.c`, `fvp_serial.c`).

## Interface
- `[fvp_boot.h:fvp_board_initialize]`
- `[fvp_boot.h:CONFIG_SYS_CLOCK_HW_CYCLES_PER_SEC]`
- `[fvp_boot.c:arm_el_init]`
- `[fvp_boot.c:arm_boot]`
- `[fvp_serial.c:arm_earlyserialinit]`
- `[fvp_serial.c:arm_serialinit]`
- `[fvp_serial.c:up_putc]`
- `[CMakeLists.txt:target_sources]`
- `[Kconfig:CONFIG_ARCH_CHIP_FVP_R52]`
- `[Make.defs:CHIP_CSRCS]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
