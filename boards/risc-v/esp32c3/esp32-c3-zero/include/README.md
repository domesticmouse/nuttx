# `esp32-c3-zero/include` Component (`boards/risc-v/esp32c3/esp32-c3-zero/include`)

## Overview
Board-level public headers (`include`) for `esp32-c3-zero` (`risc-v/esp32c3`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_NGPIOOUT]` Hardware/board configuration macros (`BOARD_NGPIOOUT`, `BOARD_NGPIOINT`, `BUTTON_BOOT`)

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh esp32-c3-zero:nsh && make`
