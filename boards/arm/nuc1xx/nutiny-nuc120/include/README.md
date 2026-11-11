# `nutiny-nuc120/include` Component (`boards/arm/nuc1xx/nutiny-nuc120/include`)

## Overview
Board-level public headers (`include`) for `nutiny-nuc120` (`arm/nuc1xx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_XTALHI_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTALHI_FREQUENCY`, `BOARD_XTALLO_FREQUENCY`, `BOARD_PLL_FIN`, `BOARD_PLL_FB_DV`, `BOARD_PLL_NF`, `BOARD_PLL_IN_DV` (+18 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh nutiny-nuc120:nsh && make`
