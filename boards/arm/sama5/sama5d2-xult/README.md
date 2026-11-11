# `sama5d2-xult` Board Support Package (`boards/arm/sama5/sama5d2-xult`)

## Overview
Board Support Package (BSP) blueprint for `sama5d2-xult` (`arm` / `sama5`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `netnsh`, `nsh`, `sdmmcnsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `sama5d2-xult` (`arm/sama5`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 7 header file(s). Key symbols: `[board.h:BOARD_MAINOSC_FREQUENCY]` Hardware/board configuration macros (`BOARD_MAINOSC_FREQUENCY`, `BOARD_SLOWCLK_FREQUENCY`, `BOARD_UPLL_FREQUENCY`, `BOARD_LCDC_OUTPUT_BPP`, `BOARD_LCDC_WIDTH`, `BOARD_LCDC_HEIGHT` (+136 more)), `[board_384mhz.h:BOARD_CKGR_MOR_MOSCXTST]` Hardware/board configuration macros (`BOARD_CKGR_MOR_MOSCXTST`, `BOARD_CKGR_PLLAR_COUNT`, `BOARD_CKGR_PLLAR_OUT`, `BOARD_CKGR_PLLAR_MUL`, `BOARD_PMC_MCKR_CSS`, `BOARD_PMC_MCKR_PRES` (+20 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `sama5d2-xult` (`arm/sama5`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 20 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[sama5d2-xult.h:sam_bringup]` Public declaration `sam_bringup()`.
