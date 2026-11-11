# esp32p4 (`nuttx/arch/risc-v/src/esp32p4`)

## Overview
Hardware abstraction and architecture package for `esp32p4` (Maximum Supported ESP32-P4 eFuse Block Revision (eFuse Block Rev v0.99); Cache config) under `nuttx/arch/risc-v/src/esp32p4`, providing 0 header file(s) and 1 source file(s) (including `esp_chip_rev.c`).

## Interface
- `[esp_chip_rev.c:esp_chip_revision_check]`
- `[CMakeLists.txt:target_sources]`
- `[Kconfig:CONFIG_ESP32P4_SELECTS_REV_LESS_V3]`
- `[Kconfig:CONFIG_ESP32P4_REV_MIN_0]`
- `[Kconfig:CONFIG_ESP32P4_REV_MIN_1]`
- `[Kconfig:CONFIG_ESP32P4_REV_MIN_100]`
- `[Kconfig:CONFIG_ESP32P4_REV_MIN_300]`
- `[Kconfig:CONFIG_ESP32P4_REV_MIN_301]`
- `[Kconfig:CONFIG_ESP32P4_REV_MIN_FULL]`
- `[Kconfig:CONFIG_ESP_REV_MIN_FULL]`
- `[Make.defs:CHIP_CSRCS]`

## Invariants
- `[esp_chip_rev.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation

## Side Effects
- None

## Verification
- Run: `make test`
