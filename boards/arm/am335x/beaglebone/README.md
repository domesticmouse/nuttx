# `beaglebone` Board Support Package (`boards/arm/am335x/beaglebone`)

## Overview
Board Support Package (BSP) blueprint for `beaglebone` (`arm` / `am335x`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `knsh`, `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `beaglebone` (`arm/am335x`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 3 header file(s). Key symbols: `[bin_romfsimg.h]` Board header declarations `bin_romfsimg.h`, `[board.h:USER_LED0]` Hardware/board configuration macros (`USER_LED0`, `USER_LED1`, `USER_LED2`, `USER_LED3`, `BOARD_NLEDS`, `BOARD_LED0_BIT` (+17 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `beaglebone` (`arm/am335x`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
