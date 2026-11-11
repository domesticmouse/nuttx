# `freedom-k28f/include` Component (`boards/arm/kinetis/freedom-k28f/include`)

## Overview
Board-level public headers (`include`) for `freedom-k28f` (`arm/kinetis`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_EXTAL_LP]` Hardware/board configuration macros (`BOARD_EXTAL_LP`, `BOARD_EXTAL_FREQ`, `BOARD_XTAL32_FREQ`, `BOARD_PRDIV`, `BOARD_VDIV`, `BOARD_MCG_C2_FCFTRIM` (+83 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh freedom-k28f:nsh && make`
