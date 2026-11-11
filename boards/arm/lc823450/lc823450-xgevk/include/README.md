# `lc823450-xgevk/include` Component (`boards/arm/lc823450/lc823450-xgevk/include`)

## Overview
Board-level public headers (`include`) for `lc823450-xgevk` (`arm/lc823450`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:up_init_default_mux]` Public declaration `up_init_default_mux()`
- `[board.h:LED_STARTED]` Hardware/board configuration macros (`LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED`, `LED_STACKCREATED`, `LED_INIRQ`, `LED_SIGNAL` (+4 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh lc823450-xgevk:nsh && make`
