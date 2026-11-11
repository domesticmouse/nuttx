# `esp32s3-box` Board Support Package (`boards/xtensa/esp32s3/esp32s3-box`)

## Overview
Board Support Package (BSP) blueprint for `esp32s3-box` (`xtensa` / `esp32s3`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `buttons`, `lvgl`, `lvgl-3`, `nsh`, `touchscreen`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `esp32s3-box` (`xtensa/esp32s3`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s). Key symbols: `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `BOARD_CLOCK_FREQUENCY`), `[board_memorymap.h:KIROM_START]` Hardware/board configuration macros (`KIROM_START`, `KIROM_SIZE`, `KDROM_START`, `KDROM_SIZE`, `KIRAM_START`, `KIRAM_SIZE` (+18 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `esp32s3-box` (`xtensa/esp32s3`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 10 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[esp32s3-box.h:esp32s3_bringup]` Public declaration `esp32s3_bringup()`.
