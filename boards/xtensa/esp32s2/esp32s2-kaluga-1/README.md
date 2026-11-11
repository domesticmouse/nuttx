# `esp32s2-kaluga-1` Board Support Package (`boards/xtensa/esp32s2/esp32s2-kaluga-1`)

## Overview
Board Support Package (BSP) blueprint for `esp32s2-kaluga-1` (`xtensa` / `esp32s2`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `audio`, `buttons`, `i2c`, `lvgl_ili9341`, `lvgl_st7789`, `nsh` (+4 more).

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `esp32s2-kaluga-1` (`xtensa/esp32s2`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `BOARD_CLOCK_FREQUENCY`, `BUTTON_BTN1`, `BUTTON_BTN1_BIT`, `BUTTON_BTN2`, `BUTTON_BTN2_BIT` (+29 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `esp32s2-kaluga-1` (`xtensa/esp32s2`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[esp32s2-kaluga-1.h:esp32s2_bringup]` Public declaration `esp32s2_bringup()`.
