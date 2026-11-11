# `freedom-k28f` Board Support Package (`boards/arm/kinetis/freedom-k28f`)

## Overview
Board Support Package (BSP) blueprint for `freedom-k28f` (`arm` / `kinetis`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `nshsdusb`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `freedom-k28f` (`arm/kinetis`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_EXTAL_LP]` Hardware/board configuration macros (`BOARD_EXTAL_LP`, `BOARD_EXTAL_FREQ`, `BOARD_XTAL32_FREQ`, `BOARD_PRDIV`, `BOARD_VDIV`, `BOARD_MCG_C2_FCFTRIM` (+83 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `freedom-k28f` (`arm/kinetis`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 12 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
