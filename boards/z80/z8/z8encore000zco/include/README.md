# `z8encore000zco/include` Component (`boards/z80/z8/z8encore000zco/include`)

## Overview
Board-level public headers (`include`) for `z8encore000zco` (`z80/z8`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:LED_STARTED]` Hardware/board configuration macros (`LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED`, `LED_STACKCREATED`, `LED_IDLE`, `LED_INIRQ` (+3 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh z8encore000zco:ostest && make`
