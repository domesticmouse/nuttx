# `esp32s3-eye/include` Component (`boards/xtensa/esp32s3/esp32s3-eye/include`)

## Overview
Board-level public headers (`include`) for `esp32s3-eye` (`xtensa/esp32s3`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s).

## Interface
- `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `BOARD_CLOCK_FREQUENCY`, `BOARD_NLEDS`, `BOARD_NGPIOOUT`, `BOARD_NGPIOIN`, `BOARD_NGPIOINT`)
- `[board_memorymap.h:KIROM_START]` Hardware/board configuration macros (`KIROM_START`, `KIROM_SIZE`, `KDROM_START`, `KDROM_SIZE`, `KIRAM_START`, `KIRAM_SIZE` (+18 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh esp32s3-eye:nsh && make`
