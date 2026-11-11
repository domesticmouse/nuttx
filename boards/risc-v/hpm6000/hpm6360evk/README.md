# `hpm6360evk` Board Support Package (`boards/risc-v/hpm6000/hpm6360evk`)

## Overview
Board Support Package (BSP) blueprint for `hpm6360evk` (`risc-v` / `hpm6000`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `hpm6360evk` (`risc-v/hpm6000`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:hpm6360_boardinitialize]` Public declaration `hpm6360_boardinitialize()`, `[board.h:BOARD_USERLED]` Hardware/board configuration macros (`BOARD_USERLED`, `BOARD_NLEDS`, `BOARD_USERLED_BIT`, `LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED` (+10 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `hpm6360evk` (`risc-v/hpm6000`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
