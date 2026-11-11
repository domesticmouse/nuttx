# `esp32-wrover-kit` Board Support Package (`boards/xtensa/esp32/esp32-wrover-kit`)

## Overview
Board Support Package (BSP) blueprint for `esp32-wrover-kit` (`xtensa` / `esp32`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `autopm`, `bmp180`, `buttons`, `gpio`, `lcd1602`, `leds` (+8 more).

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `esp32-wrover-kit` (`xtensa/esp32`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s). Key symbols: `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `BOARD_CLOCK_FREQUENCY`, `DISPLAY_SPI`, `DISPLAY_DC`, `DISPLAY_RST`, `DISPLAY_BCKL` (+24 more)), `[board_memorymap.h:KIROM_START]` Hardware/board configuration macros (`KIROM_START`, `KIROM_SIZE`, `KDROM_START`, `KDROM_SIZE`, `KIRAM_0_START`, `KIRAM_0_SIZE` (+24 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `esp32-wrover-kit` (`xtensa/esp32`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[esp32-wrover-kit.h:esp32_bringup]` Public declaration `esp32_bringup()`.
