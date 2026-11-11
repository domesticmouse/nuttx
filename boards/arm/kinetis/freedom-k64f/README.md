# `freedom-k64f` Board Support Package (`boards/arm/kinetis/freedom-k64f`)

## Overview
Board Support Package (BSP) blueprint for `freedom-k64f` (`arm` / `kinetis`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `cdcacm`, `demo`, `netnsh`, `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `freedom-k64f` (`arm/kinetis`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_EXTCLOCK]` Hardware/board configuration macros (`BOARD_EXTCLOCK`, `BOARD_EXTAL_FREQ`, `BOARD_XTAL32_FREQ`, `BOARD_PRDIV`, `BOARD_VDIV`, `BOARD_PLLIN_FREQ` (+63 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `freedom-k64f` (`arm/kinetis`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 14 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
