# `esp32c3-supermini` Board Support Package (`boards/risc-v/esp32c3/esp32c3-supermini`)

## Overview
Board Support Package (BSP) blueprint for `esp32c3-supermini` (`risc-v` / `esp32c3`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `gpio`, `nsh`, `usbnsh`, `wifi`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `esp32c3-supermini` (`risc-v/esp32c3`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_NGPIOOUT]` Hardware/board configuration macros (`BOARD_NGPIOOUT`, `BOARD_NGPIOINT`, `BUTTON_BOOT`, `LED_BUILTIN`).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `esp32c3-supermini` (`risc-v/esp32c3`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
