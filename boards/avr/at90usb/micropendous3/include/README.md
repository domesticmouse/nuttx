# `micropendous3/include` Component (`boards/avr/at90usb/micropendous3/include`)

## Overview
Board-level public headers (`include`) for `micropendous3` (`avr/at90usb`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_XTAL_FREQ]` Hardware/board configuration macros (`BOARD_XTAL_FREQ`, `BOARD_CPU_CLOCK`, `LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED`, `LED_STACKCREATED` (+4 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh micropendous3:hello && make`
