# `efm32-g8xx-stk/include` Component (`boards/arm/efm32/efm32-g8xx-stk/include`)

## Overview
Board-level public headers (`include`) for `efm32-g8xx-stk` (`arm/efm32`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_HAVE_HFXO]` Hardware/board configuration macros (`BOARD_HAVE_HFXO`, `BOARD_HAVE_LFXO`, `BOARD_HFRCO_FREQUENCY`, `BOARD_HFXO_FREQUENCY`, `BOARD_LFRCO_FREQUENCY`, `BOARD_LFXO_FREQUENCY` (+35 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh efm32-g8xx-stk:nsh && make`
