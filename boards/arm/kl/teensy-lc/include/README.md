# `teensy-lc/include` Component (`boards/arm/kl/teensy-lc/include`)

## Overview
Board-level public headers (`include`) for `teensy-lc` (`arm/kl`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_XTAL_FREQ]` Hardware/board configuration macros (`BOARD_XTAL_FREQ`, `BOARD_PRDIV0`, `BOARD_VDIV0`, `BOARD_PLLIN_FREQ`, `BOARD_PLLOUT_FREQ`, `BOARD_MCGPLLCLK_FREQ` (+29 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh teensy-lc:nsh && make`
