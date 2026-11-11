# `esp32p4-function-ev-board/include` Component (`boards/risc-v/esp32p4/esp32p4-function-ev-board/include`)

## Overview
Board-level public headers (`include`) for `esp32p4-function-ev-board` (`risc-v/esp32p4`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_NGPIOOUT]` Hardware/board configuration macros (`BOARD_NGPIOOUT`, `BOARD_NGPIOINT`, `BUTTON_BOOT`)

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh esp32p4-function-ev-board:nsh && make`
