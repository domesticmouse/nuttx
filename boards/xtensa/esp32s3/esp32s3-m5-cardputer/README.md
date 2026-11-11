# `esp32s3-m5-cardputer` Board Support Package (`boards/xtensa/esp32s3/esp32s3-m5-cardputer`)

## Overview
Board Support Package (BSP) blueprint for `esp32s3-m5-cardputer` (`xtensa` / `esp32s3`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `fb`, `lvgl`, `lvglterm`, `nsh`, `sdcard`, `softap` (+1 more).

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `esp32s3-m5-cardputer` (`xtensa/esp32s3`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `BOARD_CLOCK_FREQUENCY`, `CARDPUTER_GPIO_USB_DM`, `CARDPUTER_GPIO_USB_DP`, `CARDPUTER_GPIO_KB_A0`, `CARDPUTER_GPIO_KB_A1` (+29 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `esp32s3-m5-cardputer` (`xtensa/esp32s3`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[esp32s3-m5-cardputer.h:esp32s3_bringup]` Public declaration `esp32s3_bringup()`.
