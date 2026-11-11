# `stm32` Board Support Package (`boards/arm/common/stm32`)

## Overview
Board Support Package (BSP) blueprint for `stm32` (`arm` / `common`). Coordinates board initialization, headers, and tooling across `include, src`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `stm32` (`arm/common`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 50 header file(s). Key symbols: `[board_common.h:stm32_common_initialize]` Public declaration `stm32_common_initialize()`, `[board_hall3ph.h:board_hall3ph_initialize]` Public declaration `board_hall3ph_initialize()`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `stm32` (`arm/common`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 51 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
