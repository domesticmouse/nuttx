# `max32660-evsys` Board Support Package (`boards/arm/max326xx/max32660-evsys`)

## Overview
Board Support Package (BSP) blueprint for `max32660-evsys` (`arm` / `max326xx`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `max32660-evsys` (`arm/max326xx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_HAVE_X32K]` Hardware/board configuration macros (`BOARD_HAVE_X32K`, `BOARD_LED`, `BOARD_NLEDS`, `BOARD_LED_BIT`, `LED_STARTED`, `LED_HEAPALLOCATE` (+17 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `max32660-evsys` (`arm/max326xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
