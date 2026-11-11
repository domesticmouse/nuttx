# `quickfeather` Board Support Package (`boards/arm/eoss3/quickfeather`)

## Overview
Board Support Package (BSP) blueprint for `quickfeather` (`arm` / `eoss3`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `quickfeather` (`arm/eoss3`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_HCLK_FREQUENCY]` Hardware/board configuration macros (`BOARD_HCLK_FREQUENCY`, `BOARD_CPU_FREQUENCY`, `LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED`, `LED_STACKCREATED` (+9 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `quickfeather` (`arm/eoss3`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
