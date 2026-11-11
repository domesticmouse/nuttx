# `mirtoo/include` Component (`boards/mips/pic32mx/mirtoo/include`)

## Overview
Board-level public headers (`include`) for `mirtoo` (`mips/pic32mx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_FRC_FREQ]` Hardware/board configuration macros (`BOARD_FRC_FREQ`, `BOARD_FNOSC_FRCPLL`, `BOARD_POSC_DISABLED`, `BOARD_PLL_INPUT`, `BOARD_PLL_IDIV`, `BOARD_PLL_MULT` (+22 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh mirtoo:nsh && make`
