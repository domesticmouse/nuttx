# `hpm6360evk/include` Component (`boards/risc-v/hpm6000/hpm6360evk/include`)

## Overview
Board-level public headers (`include`) for `hpm6360evk` (`risc-v/hpm6000`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:hpm6360_boardinitialize]` Public declaration `hpm6360_boardinitialize()`
- `[board.h:BOARD_USERLED]` Hardware/board configuration macros (`BOARD_USERLED`, `BOARD_NLEDS`, `BOARD_USERLED_BIT`, `LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED` (+10 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh hpm6360evk:nsh && make`
