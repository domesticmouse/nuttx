# `z16f2800100zcog/include` Component (`boards/z16/z16f/z16f2800100zcog/include`)

## Overview
Board-level public headers (`include`) for `z16f2800100zcog` (`z16/z16f`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `BOARD_CLKSRC`, `BOARD_SYSTEM_FREQUENCY`, `BOARD_FLOPTION0`, `BOARD_FLOPTION1`, `BOARD_FLOPTION2` (+10 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh z16f2800100zcog:nsh && make`
