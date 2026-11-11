# `or1k/include` Component (`boards/or1k/mor1kx/or1k/include`)

## Overview
Board-level public headers (`include`) for `or1k` (`or1k/mor1kx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:LED_STARTED]` Hardware/board configuration macros (`LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED`, `LED_STACKCREATED`, `LED_INIRQ`, `LED_SIGNAL` (+2 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh or1k:nsh && make`
