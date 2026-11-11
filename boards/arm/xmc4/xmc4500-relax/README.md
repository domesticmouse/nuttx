# `xmc4500-relax` Board Support Package (`boards/arm/xmc4/xmc4500-relax`)

## Overview
Board Support Package (BSP) blueprint for `xmc4500-relax` (`arm` / `xmc4`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `xmc4500-relax` (`arm/xmc4`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_FCPU_120MHZ]` Hardware/board configuration macros (`BOARD_FCPU_120MHZ`, `WDT_CLKSRC_FOFI`, `WDT_CLKSRC_FSTDY`, `WDT_CLKSRC_FPLL`, `EXT_CLKSRC_FSYS`, `EXT_CLKSRC_FUSB` (+65 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `xmc4500-relax` (`arm/xmc4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
