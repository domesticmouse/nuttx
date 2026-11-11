# `lichee-rv-86-panel/include` Component (`boards/risc-v/allwinner-d1/lichee-rv-86-panel/include`)

## Overview
Board-level public headers (`include`) for `lichee-rv-86-panel` (`risc-v/allwinner-d1`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:LED_STARTED]` Hardware/board configuration macros (`LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED`, `LED_STACKCREATED`, `LED_INIRQ`, `LED_SIGNAL` (+2 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh lichee-rv-86-panel:nsh && make`
