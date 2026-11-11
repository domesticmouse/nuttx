# `nutiny-nuc120` Board Support Package (`boards/arm/nuc1xx/nutiny-nuc120`)

## Overview
Board Support Package (BSP) blueprint for `nutiny-nuc120` (`arm` / `nuc1xx`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `nutiny-nuc120` (`arm/nuc1xx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_XTALHI_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTALHI_FREQUENCY`, `BOARD_XTALLO_FREQUENCY`, `BOARD_PLL_FIN`, `BOARD_PLL_FB_DV`, `BOARD_PLL_NF`, `BOARD_PLL_IN_DV` (+18 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `nutiny-nuc120` (`arm/nuc1xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 3 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
