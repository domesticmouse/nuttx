# `common` Board Support Package (`boards/risc-v/esp32h2/common`)

## Overview
Board Support Package (BSP) blueprint for `common` (`risc-v` / `esp32h2`). Coordinates board initialization, headers, and tooling across `include, src`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `common` (`risc-v/esp32h2`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 12 header file(s). Key symbols: `[esp_board_adc.h:board_adc_init]` Public declaration `board_adc_init()`, `[esp_board_bmp180.h:board_bmp180_initialize]` Public declaration `board_bmp180_initialize()`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `common` (`risc-v/esp32h2`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 14 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
