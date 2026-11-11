# esp32h2 (`nuttx/arch/risc-v/src/esp32h2`)

## Overview
Hardware abstraction and architecture package for `esp32h2` under `nuttx/arch/risc-v/src/esp32h2`, providing 1 header file(s) and 2 source file(s) (including `esp_ble.h`, `esp_ble.c`, `esp_chip_rev.c`).

## Interface
- `[esp_ble.h:esp_ble_initialize]`
- `[esp_ble.c:esp_ble_initialize]`
- `[esp_chip_rev.c:esp_chip_revision_check]`
- `[CMakeLists.txt:target_sources]`
- `[Make.defs:CHIP_CSRCS]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
