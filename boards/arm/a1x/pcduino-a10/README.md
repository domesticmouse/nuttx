# `pcduino-a10` Board Support Package (`boards/arm/a1x/pcduino-a10`)

## Overview
Board Support Package (BSP) blueprint for `pcduino-a10` (`arm` / `a1x`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `pcduino-a10` (`arm/a1x`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s). Key symbols: `[board.h:BOARD_LED1]` Hardware/board configuration macros (`BOARD_LED1`, `BOARD_LED3`, `BOARD_LED4`, `BOARD_NLEDS`, `BOARD_LED1_BIT`, `BOARD_LED3_BIT` (+20 more)), `[board_memorymap.h]` Board header declarations `board_memorymap.h`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `pcduino-a10` (`arm/a1x`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
