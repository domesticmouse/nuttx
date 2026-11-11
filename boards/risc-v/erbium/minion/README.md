# `minion` Board Support Package (`boards/risc-v/erbium/minion`)

## Overview
Board Support Package (BSP) blueprint for `minion` (`risc-v` / `erbium`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `ostest`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `minion` (`risc-v/erbium`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:LED_STARTED]` Hardware/board configuration macros (`LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED`, `LED_STACKCREATED`, `LED_INIRQ`, `LED_SIGNAL` (+2 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `minion` (`risc-v/erbium`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 1 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
