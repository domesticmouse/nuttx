# `freedom-kl26z/include` Component (`boards/arm/kl/freedom-kl26z/include`)

## Overview
Board-level public headers (`include`) for `freedom-kl26z` (`arm/kl`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:kl_tsi_initialize]` Public declaration `kl_tsi_initialize()`
- `[board.h:BOARD_XTAL_FREQ]` Hardware/board configuration macros (`BOARD_XTAL_FREQ`, `BOARD_XTAL32_FREQ`, `BOARD_PRDIV0`, `BOARD_VDIV0`, `BOARD_PLLIN_FREQ`, `BOARD_PLLOUT_FREQ` (+38 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh freedom-kl26z:nsh && make`
