# `franzininho-wifi` Board Support Package (`boards/xtensa/esp32s2/franzininho-wifi`)

## Overview
Board Support Package (BSP) blueprint for `franzininho-wifi` (`xtensa` / `esp32s2`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `franzininho-wifi` (`xtensa/esp32s2`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `BOARD_CLOCK_FREQUENCY`, `BOARD_NLEDS`, `BOARD_NGPIOOUT`, `BOARD_NGPIOIN`, `BOARD_NGPIOINT`).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `franzininho-wifi` (`xtensa/esp32s2`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[franzininho-wifi.h:esp32s2_bringup]` Public declaration `esp32s2_bringup()`.
