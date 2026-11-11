# `common` Board Support Package (`boards/arm/rp2040/common`)

## Overview
Board Support Package (BSP) blueprint for `common` (`arm` / `rp2040`). Coordinates board initialization, headers, and tooling across `include, src`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `common` (`arm/rp2040`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 12 header file(s). Key symbols: `[rp2040_ads7046.h:board_ads7046_initialize]` Public declaration `board_ads7046_initialize()`, `[rp2040_bmp180.h:board_bmp180_initialize]` Public declaration `board_bmp180_initialize()`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `common` (`arm/rp2040`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 27 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
