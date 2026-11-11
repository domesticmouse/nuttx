# `breadxavr/include` Component (`boards/avr/avrdx/breadxavr/include`)

## Overview
Board-level public headers (`include`) for `breadxavr` (`avr/avrdx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:breadboard_buttons_e]` Type definition `breadboard_buttons_e`
- `[board.h:BOARD_XTAL_FREQ]` Hardware/board configuration macros (`BOARD_XTAL_FREQ`, `BOARD_CPU_CLOCK`, `LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED`, `LED_STACKCREATED` (+4 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh breadxavr:nsh && make`
