# `sama5d3-xplained` Board Support Package (`boards/arm/sama5/sama5d3-xplained`)

## Overview
Board Support Package (BSP) blueprint for `sama5d3-xplained` (`arm` / `sama5`). Coordinates board initialization, headers, and tooling across `helpers, include, src`. Includes build configurations: `bluetooth`, `bridge`, `ethernet-over-usb-2-high-speed`, `knsh`, `nsh`.

## Subdirectories & Boundaries
- [`helpers`](./helpers/README.md) - Board support component `helpers` for `sama5d3-xplained` (`arm/sama5`), containing 1 source/script file(s) (`netusb-up.sh`). Key symbols: `[netusb-up.sh]` Shell script entry point `netusb-up.sh`.
- [`include`](./include/README.md) - Board-level public headers (`include`) for `sama5d3-xplained` (`arm/sama5`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 7 header file(s). Key symbols: `[board.h:BOARD_MAINOSC_FREQUENCY]` Hardware/board configuration macros (`BOARD_MAINOSC_FREQUENCY`, `BOARD_SLOWCLK_FREQUENCY`, `BOARD_BLUE`, `BOARD_RED`, `BOARD_NLEDS`, `BOARD_BLUE_BIT` (+19 more)), `[board_384mhz.h:BOARD_CKGR_MOR_MOSCXTST]` Hardware/board configuration macros (`BOARD_CKGR_MOR_MOSCXTST`, `BOARD_CKGR_PLLAR_COUNT`, `BOARD_CKGR_PLLAR_OUT`, `BOARD_CKGR_PLLAR_MUL`, `BOARD_CKGR_PLLAR_DIV`, `BOARD_PMC_MCKR_CSS` (+20 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `sama5d3-xplained` (`arm/sama5`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 20 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
