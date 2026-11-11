# `olimex-lpc2378` Board Support Package (`boards/arm/lpc2378/olimex-lpc2378`)

## Overview
Board Support Package (BSP) blueprint for `olimex-lpc2378` (`arm` / `lpc2378`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `olimex-lpc2378` (`arm/lpc2378`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:FOSC]` Hardware/board configuration macros (`FOSC`, `FCCO`, `CCLK`, `PLL_M`, `PLL_N`, `CCLK_DIV` (+10 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `olimex-lpc2378` (`arm/lpc2378`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 1 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[lpc2378_leds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`.
