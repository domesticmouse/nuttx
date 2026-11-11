# `giant-board` Board Support Package (`boards/arm/sama5/giant-board`)

## Overview
Board Support Package (BSP) blueprint for `giant-board` (`arm` / `sama5`). Coordinates board initialization, headers, and tooling across `helpers, include, src`. Includes build configurations: `netnsh`, `nsh`, `sdmmc-net-nsh`, `sdmmcnsh`.

## Subdirectories & Boundaries
- [`helpers`](./helpers/README.md) - Board support component `helpers` for `giant-board` (`arm/sama5`), containing 1 source/script file(s) (`netusb-up.sh`). Key symbols: `[netusb-up.sh]` Shell script entry point `netusb-up.sh`.
- [`include`](./include/README.md) - Board-level public headers (`include`) for `giant-board` (`arm/sama5`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 4 header file(s). Key symbols: `[board.h:BOARD_MAINOSC_FREQUENCY]` Hardware/board configuration macros (`BOARD_MAINOSC_FREQUENCY`, `BOARD_SLOWCLK_FREQUENCY`, `BOARD_ORANGE`, `BOARD_NLEDS`, `BOARD_ORANGE_BIT`, `LED_STARTED` (+20 more)), `[board_492mhz.h:BOARD_CKGR_MOR_MOSCXTST]` Hardware/board configuration macros (`BOARD_CKGR_MOR_MOSCXTST`, `BOARD_CKGR_PLLAR_COUNT`, `BOARD_CKGR_PLLAR_OUT`, `BOARD_CKGR_PLLAR_MUL`, `BOARD_PMC_MCKR_CSS`, `BOARD_PMC_MCKR_PRES` (+22 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `giant-board` (`arm/sama5`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 15 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[giant-board.h:sam_bringup]` Public declaration `sam_bringup()`.
