# `rv32m1-vega/include` Component (`boards/risc-v/rv32m1/rv32m1-vega/include`)

## Overview
Board-level public headers (`include`) for `rv32m1-vega` (`risc-v/rv32m1`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:rv32m1_boardinitialize]` Public declaration `rv32m1_boardinitialize()`
- `[board.h:LED_STARTED]` Hardware/board configuration macros (`LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED`, `LED_STACKCREATED`, `LED_INIRQ`, `LED_SIGNAL` (+11 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh rv32m1-vega:nsh && make`
