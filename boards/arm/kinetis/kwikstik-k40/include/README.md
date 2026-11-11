# `kwikstik-k40/include` Component (`boards/arm/kinetis/kwikstik-k40/include`)

## Overview
Board-level public headers (`include`) for `kwikstik-k40` (`arm/kinetis`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_EXTAL_FREQ]` Hardware/board configuration macros (`BOARD_EXTAL_FREQ`, `BOARD_XTAL32_FREQ`, `BOARD_PRDIV`, `BOARD_VDIV`, `BOARD_PLLIN_FREQ`, `BOARD_PLLOUT_FREQ` (+41 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh kwikstik-k40:ostest && make`
