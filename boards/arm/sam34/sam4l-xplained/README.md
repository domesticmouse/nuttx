# `sam4l-xplained` Board Support Package (`boards/arm/sam34/sam4l-xplained`)

## Overview
Board Support Package (BSP) blueprint for `sam4l-xplained` (`arm` / `sam34`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `sam4l-xplained` (`arm/sam34`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_SYSCLK_SOURCE_DFLL0]` Hardware/board configuration macros (`BOARD_SYSCLK_SOURCE_DFLL0`, `BOARD_RCSYS_FREQUENCY`, `BOARD_RC32K_FREQUENCY`, `BOARD_RC80M_FREQUENCY`, `BOARD_RCFAST4M_FREQUENCY`, `BOARD_RCFAST8M_FREQUENCY` (+46 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `sam4l-xplained` (`arm/sam34`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 9 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
