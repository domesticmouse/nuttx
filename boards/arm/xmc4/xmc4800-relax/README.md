# `xmc4800-relax` Board Support Package (`boards/arm/xmc4/xmc4800-relax`)

## Overview
Board Support Package (BSP) blueprint for `xmc4800-relax` (`arm` / `xmc4`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `xmc4800-relax` (`arm/xmc4`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_FCPU_144MHZ]` Hardware/board configuration macros (`BOARD_FCPU_144MHZ`, `WDT_CLKSRC_FOFI`, `WDT_CLKSRC_FSTDY`, `WDT_CLKSRC_FPLL`, `EXT_CLKSRC_FSYS`, `EXT_CLKSRC_FUSB` (+101 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `xmc4800-relax` (`arm/xmc4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
