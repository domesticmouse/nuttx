# `p112/include` Component (`boards/z80/z180/p112/include`)

## Overview
Board-level public headers (`include`) for `p112` (`z80/z180`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:Z180_BOARD_XTAL]` Hardware/board configuration macros (`Z180_BOARD_XTAL`, `Z180_SYSCLOCK`)

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh p112:ostest && make`
