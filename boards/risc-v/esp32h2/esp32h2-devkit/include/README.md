# `esp32h2-devkit/include` Component (`boards/risc-v/esp32h2/esp32h2-devkit/include`)

## Overview
Board-level public headers (`include`) for `esp32h2-devkit` (`risc-v/esp32h2`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_NGPIOOUT]` Hardware/board configuration macros (`BOARD_NGPIOOUT`, `BOARD_NGPIOINT`, `BUTTON_BOOT`)

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh esp32h2-devkit:nsh && make`
