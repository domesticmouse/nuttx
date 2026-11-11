# `teensy-3.x` Board Support Package (`boards/arm/kinetis/teensy-3.x`)

## Overview
Board Support Package (BSP) blueprint for `teensy-3.x` (`arm` / `kinetis`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `usbnsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `teensy-3.x` (`arm/kinetis`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_EXTAL_LP]` Hardware/board configuration macros (`BOARD_EXTAL_LP`, `BOARD_FRDIV`, `BOARD_EXTAL_FREQ`, `BOARD_XTAL32_FREQ`, `BOARD_PRDIV`, `BOARD_VDIV` (+48 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `teensy-3.x` (`arm/kinetis`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
