# `esp32-audio-kit` Board Support Package (`boards/xtensa/esp32/esp32-audio-kit`)

## Overview
Board Support Package (BSP) blueprint for `esp32-audio-kit` (`xtensa` / `esp32`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `audio`, `nsh`, `wifi`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `esp32-audio-kit` (`xtensa/esp32`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s). Key symbols: `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `BOARD_CLOCK_FREQUENCY`, `ES8388_I2C_CCLK`, `ES8388_I2C_CDATA`, `ES8388_I2S_MCLK`, `ES8388_I2S_SCLK` (+9 more)), `[board_memorymap.h:KIROM_START]` Hardware/board configuration macros (`KIROM_START`, `KIROM_SIZE`, `KDROM_START`, `KDROM_SIZE`, `KIRAM_0_START`, `KIRAM_0_SIZE` (+24 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `esp32-audio-kit` (`xtensa/esp32`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[esp32-audio-kit.h:esp32_bringup]` Public declaration `esp32_bringup()`.
