# `spresense` Board Support Package (`boards/arm/cxd56xx/spresense`)

## Overview
Board Support Package (BSP) blueprint for `spresense` (`arm` / `cxd56xx`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `audio`, `audio_sdk`, `camera`, `charger`, `coremark`, `elf` (+22 more).

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `spresense` (`arm/cxd56xx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 41 header file(s). Key symbols: `[board.h:cxd56_boardinitialize]` Public declaration `cxd56_boardinitialize()`, `[board.h:board_power_device]` Type definition `board_power_device`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `spresense` (`arm/cxd56xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 19 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
