# `amber/include` Component (`boards/avr/atmega/amber/include`)

## Overview
Board-level public headers (`include`) for `amber` (`avr/atmega`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_XTAL_FREQ]` Hardware/board configuration macros (`BOARD_XTAL_FREQ`, `BOARD_CPU_CLOCK`, `BOARD_TOSCK_CLOCK`, `LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED` (+5 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh amber:hello && make`
