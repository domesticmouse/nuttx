# `esp32c6-devkitc/include` Component (`boards/risc-v/esp32c6/esp32c6-devkitc/include`)

## Overview
Board-level public headers (`include`) for `esp32c6-devkitc` (`risc-v/esp32c6`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_NGPIOOUT]` Hardware/board configuration macros (`BOARD_NGPIOOUT`, `BOARD_NGPIOINT`, `BUTTON_BOOT`)

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh esp32c6-devkitc:nsh && make`
