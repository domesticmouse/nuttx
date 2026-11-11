# `teensy-lc` Board Support Package (`boards/arm/kl/teensy-lc`)

## Overview
Board Support Package (BSP) blueprint for `teensy-lc` (`arm` / `kl`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `teensy-lc` (`arm/kl`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_XTAL_FREQ]` Hardware/board configuration macros (`BOARD_XTAL_FREQ`, `BOARD_PRDIV0`, `BOARD_VDIV0`, `BOARD_PLLIN_FREQ`, `BOARD_PLLOUT_FREQ`, `BOARD_MCGPLLCLK_FREQ` (+29 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `teensy-lc` (`arm/kl`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
