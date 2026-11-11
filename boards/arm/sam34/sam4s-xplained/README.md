# `sam4s-xplained` Board Support Package (`boards/arm/sam34/sam4s-xplained`)

## Overview
Board Support Package (BSP) blueprint for `sam4s-xplained` (`arm` / `sam34`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `sam4s-xplained` (`arm/sam34`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_CKGR_MOR_MOSCXTST]` Hardware/board configuration macros (`BOARD_CKGR_MOR_MOSCXTST`, `BOARD_MAINOSC_FREQUENCY`, `BOARD_CKGR_PLLAR_MUL`, `BOARD_CKGR_PLLAR_DIV`, `BOARD_CKGR_PLLAR_COUNT`, `BOARD_PLLA_FREQUENCY` (+27 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `sam4s-xplained` (`arm/sam34`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 6 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
