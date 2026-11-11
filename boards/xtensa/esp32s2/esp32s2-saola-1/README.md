# `esp32s2-saola-1` Board Support Package (`boards/xtensa/esp32s2/esp32s2-saola-1`)

## Overview
Board Support Package (BSP) blueprint for `esp32s2-saola-1` (`xtensa` / `esp32s2`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `adc`, `audio`, `buttons`, `coremark`, `crypto`, `cxx` (+29 more).

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `esp32s2-saola-1` (`xtensa/esp32s2`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `BOARD_CLOCK_FREQUENCY`, `BUTTON_BTN1`, `BUTTON_BTN1_BIT`, `NUM_BUTTONS`, `BOARD_NLEDS` (+3 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `esp32s2-saola-1` (`xtensa/esp32s2`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 10 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
