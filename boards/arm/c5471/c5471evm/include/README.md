# `c5471evm/include` Component (`boards/arm/c5471/c5471evm/include`)

## Overview
Board-level public headers (`include`) for `c5471evm` (`arm/c5471`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:C5471_CLOCK]` Hardware/board configuration macros (`C5471_CLOCK`, `LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED`, `LED_STACKCREATED`, `LED_INIRQ` (+3 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh c5471evm:nsh && make`
