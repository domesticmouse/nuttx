# `esk32` Board Support Package (`boards/arm/ht32f491x3/esk32`)

## Overview
Board Support Package (BSP) blueprint for `esk32` (`arm` / `ht32f491x3`). Coordinates board initialization, headers, and tooling across `include, src, tools`. Includes build configurations: `nsh`, `pwm`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `esk32` (`arm/ht32f491x3`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:ht32f491x3_clockconfig]` Public declaration `ht32f491x3_clockconfig()`, `[board.h:ht32f491x3_boardinitialize]` Public declaration `ht32f491x3_boardinitialize()`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `esk32` (`arm/ht32f491x3`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
- [`tools`](./tools/README.md) - Board support component `tools` for `esk32` (`arm/ht32f491x3`), containing 2 source/script file(s) (`flash.py, flash.sh`). Key symbols: `[flash.py:is_windows_host]` Python function `is_windows_host()`, `[flash.py:is_wsl]` Python function `is_wsl()`.
