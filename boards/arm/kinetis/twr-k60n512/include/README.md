# `twr-k60n512/include` Component (`boards/arm/kinetis/twr-k60n512/include`)

## Overview
Board-level public headers (`include`) for `twr-k60n512` (`arm/kinetis`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_EXTCLOCK]` Hardware/board configuration macros (`BOARD_EXTCLOCK`, `BOARD_EXTAL_FREQ`, `BOARD_XTAL32_FREQ`, `BOARD_PRDIV`, `BOARD_VDIV`, `BOARD_PLLIN_FREQ` (+41 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh twr-k60n512:nsh && make`
