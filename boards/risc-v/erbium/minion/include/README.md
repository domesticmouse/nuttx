# `minion/include` Component (`boards/risc-v/erbium/minion/include`)

## Overview
Board-level public headers (`include`) for `minion` (`risc-v/erbium`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:LED_STARTED]` Hardware/board configuration macros (`LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED`, `LED_STACKCREATED`, `LED_INIRQ`, `LED_SIGNAL` (+2 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh minion:nsh && make`
