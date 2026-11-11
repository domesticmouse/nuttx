# `lpcxpresso-lpc54628` Board Support Package (`boards/arm/lpc54xx/lpcxpresso-lpc54628`)

## Overview
Board Support Package (BSP) blueprint for `lpcxpresso-lpc54628` (`arm` / `lpc54xx`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `fb`, `lvgl`, `netnsh`, `nsh`, `nxwm`, `pwfb` (+3 more).

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `lpcxpresso-lpc54628` (`arm/lpc54xx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_PLL_SOURCE]` Hardware/board configuration macros (`BOARD_PLL_SOURCE`, `BOARD_PLL_FIN`, `BOARD_PLL_CLKSEL`, `BOARD_PLL_SELI`, `BOARD_PLL_SELP`, `BOARD_PLL_SELR` (+80 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `lpcxpresso-lpc54628` (`arm/lpc54xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 11 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
