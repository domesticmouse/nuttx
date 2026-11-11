# `lpcxpresso-lpc54628/include` Component (`boards/arm/lpc54xx/lpcxpresso-lpc54628/include`)

## Overview
Board-level public headers (`include`) for `lpcxpresso-lpc54628` (`arm/lpc54xx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_PLL_SOURCE]` Hardware/board configuration macros (`BOARD_PLL_SOURCE`, `BOARD_PLL_FIN`, `BOARD_PLL_CLKSEL`, `BOARD_PLL_SELI`, `BOARD_PLL_SELP`, `BOARD_PLL_SELR` (+80 more))

## Invariants
- `[board.h:#error]` Compile-time guard: `Missing SYSTICK divider`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh lpcxpresso-lpc54628:nsh && make`
