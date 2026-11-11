# `arduino-mega2560/include` Component (`boards/avr/atmega/arduino-mega2560/include`)

## Overview
Board-level public headers (`include`) for `arduino-mega2560` (`avr/atmega`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_XTAL_FREQ]` Hardware/board configuration macros (`BOARD_XTAL_FREQ`, `BOARD_CPU_CLOCK`)

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh arduino-mega2560:nsh && make`
