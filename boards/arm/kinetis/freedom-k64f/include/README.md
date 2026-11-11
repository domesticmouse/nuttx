# `freedom-k64f/include` Component (`boards/arm/kinetis/freedom-k64f/include`)

## Overview
Board-level public headers (`include`) for `freedom-k64f` (`arm/kinetis`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_EXTCLOCK]` Hardware/board configuration macros (`BOARD_EXTCLOCK`, `BOARD_EXTAL_FREQ`, `BOARD_XTAL32_FREQ`, `BOARD_PRDIV`, `BOARD_VDIV`, `BOARD_PLLIN_FREQ` (+63 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh freedom-k64f:nsh && make`
