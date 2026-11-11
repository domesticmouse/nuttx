# `esp32c6-xiao` Board Support Package (`boards/risc-v/esp32c6/esp32c6-xiao`)

## Overview
Board Support Package (BSP) blueprint for `esp32c6-xiao` (`risc-v` / `esp32c6`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `gpio`, `nsh`, `usbnsh`, `wifi`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `esp32c6-xiao` (`risc-v/esp32c6`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h]` Board header declarations `board.h`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `esp32c6-xiao` (`risc-v/esp32c6`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
