# `teensy-3.x/include` Component (`boards/arm/kinetis/teensy-3.x/include`)

## Overview
Board-level public headers (`include`) for `teensy-3.x` (`arm/kinetis`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_EXTAL_LP]` Hardware/board configuration macros (`BOARD_EXTAL_LP`, `BOARD_FRDIV`, `BOARD_EXTAL_FREQ`, `BOARD_XTAL32_FREQ`, `BOARD_PRDIV`, `BOARD_VDIV` (+48 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh teensy-3.x:nsh && make`
