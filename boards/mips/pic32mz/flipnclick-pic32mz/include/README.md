# `flipnclick-pic32mz/include` Component (`boards/mips/pic32mz/flipnclick-pic32mz/include`)

## Overview
Board-level public headers (`include`) for `flipnclick-pic32mz` (`mips/pic32mz`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_POSC_FREQ]` Hardware/board configuration macros (`BOARD_POSC_FREQ`, `BOARD_SOSC_FREQ`, `BOARD_FNOSC_SPLL`, `BOARD_POSC_ECMODE`, `BOARD_POSC_SWITCH`, `BOARD_PLL_INPUT` (+60 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh flipnclick-pic32mz:nsh && make`
