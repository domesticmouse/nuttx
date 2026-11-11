# `hpm6750evk2` Board Support Package (`boards/risc-v/hpm6750/hpm6750evk2`)

## Overview
Board Support Package (BSP) blueprint for `hpm6750evk2` (`risc-v` / `hpm6750`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `hpm6750evk2` (`risc-v/hpm6750`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:hpm6750_boardinitialize]` Public declaration `hpm6750_boardinitialize()`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `hpm6750evk2` (`risc-v/hpm6750`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 3 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
