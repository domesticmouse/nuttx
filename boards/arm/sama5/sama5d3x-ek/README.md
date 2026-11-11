# `sama5d3x-ek` Board Support Package (`boards/arm/sama5/sama5d3x-ek`)

## Overview
Board Support Package (BSP) blueprint for `sama5d3x-ek` (`arm` / `sama5`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `demo`, `hello`, `norboot`, `nsh`, `nx`, `nxplayer` (+2 more).

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `sama5d3x-ek` (`arm/sama5`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 6 header file(s). Key symbols: `[board.h:BOARD_MAINOSC_FREQUENCY]` Hardware/board configuration macros (`BOARD_MAINOSC_FREQUENCY`, `BOARD_SLOWCLK_FREQUENCY`, `BOARD_LCDC_OUTPUT_BPP`, `BOARD_LCDC_WIDTH`, `BOARD_LCDC_HEIGHT`, `BOARD_LCDC_PIXCLK_INV` (+41 more)), `[board_384mhz.h:BOARD_CKGR_MOR_MOSCXTST]` Hardware/board configuration macros (`BOARD_CKGR_MOR_MOSCXTST`, `BOARD_CKGR_PLLAR_COUNT`, `BOARD_CKGR_PLLAR_OUT`, `BOARD_CKGR_PLLAR_MUL`, `BOARD_CKGR_PLLAR_DIV`, `BOARD_PMC_MCKR_CSS` (+20 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `sama5d3x-ek` (`arm/sama5`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 23 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
