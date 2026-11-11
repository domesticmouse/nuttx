# `chipkit-wifire/include` Component (`boards/mips/pic32mz/chipkit-wifire/include`)

## Overview
Board-level public headers (`include`) for `chipkit-wifire` (`mips/pic32mz`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_POSC_FREQ]` Hardware/board configuration macros (`BOARD_POSC_FREQ`, `BOARD_SOSC_FREQ`, `BOARD_FNOSC_SPLL`, `BOARD_POSC_ECMODE`, `BOARD_POSC_SWITCH`, `BOARD_PLL_INPUT` (+52 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh chipkit-wifire:nsh && make`
