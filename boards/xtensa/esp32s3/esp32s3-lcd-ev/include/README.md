# `esp32s3-lcd-ev/include` Component (`boards/xtensa/esp32s3/esp32s3-lcd-ev/include`)

## Overview
Board-level public headers (`include`) for `esp32s3-lcd-ev` (`xtensa/esp32s3`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s).

## Interface
- `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `BOARD_CLOCK_FREQUENCY`, `ES8311_I2C_FREQ`, `ES8311_I2C_ADDR`)
- `[board_memorymap.h:KIROM_START]` Hardware/board configuration macros (`KIROM_START`, `KIROM_SIZE`, `KDROM_START`, `KDROM_SIZE`, `KIRAM_START`, `KIRAM_SIZE` (+18 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh esp32s3-lcd-ev:nsh && make`
