# `esp32-audio-kit/include` Component (`boards/xtensa/esp32/esp32-audio-kit/include`)

## Overview
Board-level public headers (`include`) for `esp32-audio-kit` (`xtensa/esp32`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s).

## Interface
- `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `BOARD_CLOCK_FREQUENCY`, `ES8388_I2C_CCLK`, `ES8388_I2C_CDATA`, `ES8388_I2S_MCLK`, `ES8388_I2S_SCLK` (+9 more))
- `[board_memorymap.h:KIROM_START]` Hardware/board configuration macros (`KIROM_START`, `KIROM_SIZE`, `KDROM_START`, `KDROM_SIZE`, `KIRAM_0_START`, `KIRAM_0_SIZE` (+24 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh esp32-audio-kit:nsh && make`
