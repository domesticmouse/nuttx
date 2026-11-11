# `csk6011a-nano` Board Support Package (`boards/arm/csk6/csk6011a-nano`)

## Overview
Board Support Package (BSP) blueprint for `csk6011a-nano` (`arm` / `csk6`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `csk6011a-nano` (`arm/csk6`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:CSK6_SYSTICK_CLOCK]` Hardware/board configuration macros (`CSK6_SYSTICK_CLOCK`).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `csk6011a-nano` (`arm/csk6`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 1 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
