# `xiao-ra4m1` Board Support Package (`boards/arm/ra4/xiao-ra4m1`)

## Overview
Board Support Package (BSP) blueprint for `xiao-ra4m1` (`arm` / `ra4`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `combo`, `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `xiao-ra4m1` (`arm/ra4`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:RA_CKSEL]` Hardware/board configuration macros (`RA_CKSEL`, `RA_HOCOEN`, `RA_HOCO_FREQUENCY`, `RA_ICK_DIV`, `RA_ICLK_FREQUENCY`, `RA_FCK_DIV` (+36 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `xiao-ra4m1` (`arm/ra4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 6 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
