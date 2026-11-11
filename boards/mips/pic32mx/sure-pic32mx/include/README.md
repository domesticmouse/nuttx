# `sure-pic32mx/include` Component (`boards/mips/pic32mx/sure-pic32mx/include`)

## Overview
Board-level public headers (`include`) for `sure-pic32mx` (`mips/pic32mx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_POSC_FREQ]` Hardware/board configuration macros (`BOARD_POSC_FREQ`, `BOARD_SOSC_FREQ`, `BOARD_FNOSC_POSCPLL`, `BOARD_POSC_HSMODE`, `BOARD_PLL_INPUT`, `BOARD_PLL_IDIV` (+29 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh sure-pic32mx:nsh && make`
