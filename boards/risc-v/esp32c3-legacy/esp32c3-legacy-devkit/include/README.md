# `esp32c3-legacy-devkit/include` Component (`boards/risc-v/esp32c3-legacy/esp32c3-legacy-devkit/include`)

## Overview
Board-level public headers (`include`) for `esp32c3-legacy-devkit` (`risc-v/esp32c3-legacy`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s).

## Interface
- `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `BOARD_NGPIOOUT`, `BOARD_NGPIOINT`)
- `[board_memorymap.h:KIROM_START]` Hardware/board configuration macros (`KIROM_START`, `KIROM_SIZE`, `KDROM_START`, `KDROM_SIZE`, `KIRAM_START`, `KIRAM_SIZE` (+18 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh esp32c3-legacy-devkit:nsh && make`
