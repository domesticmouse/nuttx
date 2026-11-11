# `orangepi-5-pro` Board Support Package (`boards/arm64/rk3588/orangepi-5-pro`)

## Overview
Board Support Package (BSP) blueprint for `orangepi-5-pro` (`arm64` / `rk3588`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `ostest`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `orangepi-5-pro` (`arm64/rk3588`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h]` Board header declarations `board.h`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `orangepi-5-pro` (`arm64/rk3588`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
