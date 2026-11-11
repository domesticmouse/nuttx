# `common` Board Support Package (`boards/xtensa/esp32s2/common`)

## Overview
Board Support Package (BSP) blueprint for `common` (`xtensa` / `esp32s2`). Coordinates board initialization, headers, and tooling across `include, src`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `common` (`xtensa/esp32s2`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 10 header file(s). Key symbols: `[esp32s2_board_adc.h:board_adc_init]` Public declaration `board_adc_init()`, `[esp32s2_board_pcnt.h:board_pcnt_initialize]` Public declaration `board_pcnt_initialize()`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `common` (`xtensa/esp32s2`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 17 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
