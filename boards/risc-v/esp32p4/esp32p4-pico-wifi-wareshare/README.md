# `esp32p4-pico-wifi-wareshare` Board Support Package (`boards/risc-v/esp32p4/esp32p4-pico-wifi-wareshare`)

## Overview
Board Support Package (BSP) blueprint for `esp32p4-pico-wifi-wareshare` (`risc-v` / `esp32p4`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `spiflash`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `esp32p4-pico-wifi-wareshare` (`risc-v/esp32p4`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_NGPIOOUT]` Hardware/board configuration macros (`BOARD_NGPIOOUT`, `BOARD_NGPIOINT`, `BUTTON_BOOT`).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `esp32p4-pico-wifi-wareshare` (`risc-v/esp32p4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 6 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
