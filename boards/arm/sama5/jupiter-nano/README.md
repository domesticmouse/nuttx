# `jupiter-nano` Board Support Package (`boards/arm/sama5/jupiter-nano`)

## Overview
Board Support Package (BSP) blueprint for `jupiter-nano` (`arm` / `sama5`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `netnsh`, `nsh`, `sdmmc-nsh-net-resolvconf`, `sdmmcnsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `jupiter-nano` (`arm/sama5`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 7 header file(s). Key symbols: `[board.h:BOARD_MAINOSC_FREQUENCY]` Hardware/board configuration macros (`BOARD_MAINOSC_FREQUENCY`, `BOARD_SLOWCLK_FREQUENCY`, `BOARD_UPLL_FREQUENCY`, `BOARD_BLUE`, `BOARD_BLUE_BIT`, `BOARD_NLEDS` (+34 more)), `[board_384mhz.h:BOARD_CKGR_MOR_MOSCXTST]` Hardware/board configuration macros (`BOARD_CKGR_MOR_MOSCXTST`, `BOARD_CKGR_PLLAR_COUNT`, `BOARD_CKGR_PLLAR_OUT`, `BOARD_CKGR_PLLAR_MUL`, `BOARD_PMC_MCKR_CSS`, `BOARD_PMC_MCKR_PRES` (+20 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `jupiter-nano` (`arm/sama5`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 21 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[jupiter-nano.h:sam_bringup]` Public declaration `sam_bringup()`.
