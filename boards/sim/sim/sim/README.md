# `sim` Board Support Package (`boards/sim/sim/sim`)

## Overview
Board Support Package (BSP) blueprint for `sim` (`sim` / `sim`). Coordinates board initialization, headers, and tooling across `configs, include, src`. Includes build configurations: `adb`, `alsa`, `asan`, `baromonitor`, `bas`, `bastest` (+105 more).

## Subdirectories & Boundaries
- [`configs`](./configs/README.md) - Intermediate blueprint for `sim/configs` (`sim/sim`), grouping `citest`.
- [`include`](./include/README.md) - Board-level public headers (`include`) for `sim` (`sim/sim`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h]` Board header declarations `board.h`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `sim` (`sim/sim`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 10 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
