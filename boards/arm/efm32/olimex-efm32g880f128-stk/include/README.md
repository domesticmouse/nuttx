# `olimex-efm32g880f128-stk/include` Component (`boards/arm/efm32/olimex-efm32g880f128-stk/include`)

## Overview
Board-level public headers (`include`) for `olimex-efm32g880f128-stk` (`arm/efm32`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_HAVE_HFXO]` Hardware/board configuration macros (`BOARD_HAVE_HFXO`, `BOARD_HAVE_LFXO`, `BOARD_HFRCO_FREQUENCY`, `BOARD_HFXO_FREQUENCY`, `BOARD_LFRCO_FREQUENCY`, `BOARD_LFXO_FREQUENCY` (+48 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh olimex-efm32g880f128-stk:nsh && make`
