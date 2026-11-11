# `t3-gem-o1` Board Support Package (`boards/arm/am67/t3-gem-o1`)

## Overview
Board Support Package (BSP) blueprint for `t3-gem-o1` (`arm` / `am67`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `netnsh`, `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `t3-gem-o1` (`arm/am67`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h]` Board header declarations `board.h`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `t3-gem-o1` (`arm/am67`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 6 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
