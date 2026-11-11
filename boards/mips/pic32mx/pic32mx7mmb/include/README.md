# `pic32mx7mmb/include` Component (`boards/mips/pic32mx/pic32mx7mmb/include`)

## Overview
Board-level public headers (`include`) for `pic32mx7mmb` (`mips/pic32mx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_POSC_FREQ]` Hardware/board configuration macros (`BOARD_POSC_FREQ`, `BOARD_SOSC_FREQ`, `BOARD_FNOSC_POSCPLL`, `BOARD_POSC_XTMODE`, `BOARD_SOSC_ENABLE`, `BOARD_SOSC_IESO` (+28 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh pic32mx7mmb:nsh && make`
