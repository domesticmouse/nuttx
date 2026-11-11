# `esp32c3-xiao/include` Component (`boards/risc-v/esp32c3/esp32c3-xiao/include`)

## Overview
Board-level public headers (`include`) for `esp32c3-xiao` (`risc-v/esp32c3`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_NGPIOOUT]` Hardware/board configuration macros (`BOARD_NGPIOOUT`, `BOARD_NGPIOINT`)

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh esp32c3-xiao:nsh && make`
