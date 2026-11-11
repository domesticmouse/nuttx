# rk3588 (`nuttx/arch/arm64/src/rk3588`)

## Overview
Hardware abstraction and architecture package for `rk3588` under `nuttx/arch/arm64/src/rk3588`, providing 2 header file(s) and 2 source file(s) (including `chip.h`, `rk3588_boot.h`, `rk3588_boot.c`, `rk3588_serial.c`).

## Interface
- `[rk3588_boot.h:rk3588_memory_initialize]`
- `[rk3588_boot.h:rk3588_board_initialize]`
- `[rk3588_boot.c:arm64_el_init]`
- `[rk3588_boot.c:arm64_chip_boot]`
- `[rk3588_boot.c:arm64_netinitialize]`
- `[rk3588_serial.c:arm64_earlyserialinit]`
- `[rk3588_serial.c:arm64_serialinit]`
- `[CMakeLists.txt:target_sources]`
- `[Make.defs:CHIP_CSRCS]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
