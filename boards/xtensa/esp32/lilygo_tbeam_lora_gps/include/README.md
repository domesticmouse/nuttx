# `lilygo_tbeam_lora_gps/include` Component (`boards/xtensa/esp32/lilygo_tbeam_lora_gps/include`)

## Overview
Board-level public headers (`include`) for `lilygo_tbeam_lora_gps` (`xtensa/esp32`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s).

## Interface
- `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `BOARD_CLOCK_FREQUENCY`, `BOARD_NLEDS`, `BOARD_NGPIOOUT`, `BOARD_NGPIOIN`, `BOARD_NGPIOINT`)
- `[board_memorymap.h:KIROM_START]` Hardware/board configuration macros (`KIROM_START`, `KIROM_SIZE`, `KDROM_START`, `KDROM_SIZE`, `KIRAM_0_START`, `KIRAM_0_SIZE` (+24 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh lilygo_tbeam_lora_gps:nsh && make`
