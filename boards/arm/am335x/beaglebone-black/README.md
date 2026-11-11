# `beaglebone-black` Board Support Package (`boards/arm/am335x/beaglebone-black`)

## Overview
Board Support Package (BSP) blueprint for `beaglebone-black` (`arm` / `am335x`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `lcd`, `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `beaglebone-black` (`arm/am335x`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s). Key symbols: `[board.h:USER_LED0]` Hardware/board configuration macros (`USER_LED0`, `USER_LED1`, `USER_LED2`, `USER_LED3`, `BOARD_NLEDS`, `BOARD_LED0_BIT` (+17 more)), `[board_memorymap.h]` Board header declarations `board_memorymap.h`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `beaglebone-black` (`arm/am335x`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 6 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
