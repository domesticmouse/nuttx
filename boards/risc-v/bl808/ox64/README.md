# `ox64` Board Support Package (`boards/risc-v/bl808/ox64`)

## Overview
Board Support Package (BSP) blueprint for `ox64` (`risc-v` / `bl808`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `adc`, `nsh`, `spi`, `timer`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `ox64` (`risc-v/bl808`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s). Key symbols: `[board.h:bl808_boardinitialize]` Public declaration `bl808_boardinitialize()`, `[board.h:BOARD_LED1_BIT]` Hardware/board configuration macros (`BOARD_LED1_BIT`, `BOARD_LED2_BIT`, `BOARD_LED3_BIT`, `LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED` (+6 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `ox64` (`risc-v/bl808`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 3 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[bl808_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`.
