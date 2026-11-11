# `pic32mx-starterkit/include` Component (`boards/mips/pic32mx/pic32mx-starterkit/include`)

## Overview
Board-level public headers (`include`) for `pic32mx-starterkit` (`mips/pic32mx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_POSC_FREQ]` Hardware/board configuration macros (`BOARD_POSC_FREQ`, `BOARD_SOSC_FREQ`, `BOARD_FNOSC_POSCPLL`, `BOARD_POSC_HSMODE`, `BOARD_PLL_INPUT`, `BOARD_PLL_IDIV` (+26 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh pic32mx-starterkit:nsh && make`
