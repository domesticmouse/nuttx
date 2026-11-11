# `rm57l843-launchxl2/include` Component (`boards/arm/rm57/rm57l843-launchxl2/include`)

## Overview
Board-level public headers (`include`) for `rm57l843-launchxl2` (`arm/rm57`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_FCLKIN_FREQUENCY]` Hardware/board configuration macros (`BOARD_FCLKIN_FREQUENCY`, `BOARD_PLL_NR`, `BOARD_PLL_PLLMUL`, `BOARD_PLL_OD`, `BOARD_PLL_R`, `BOARD_PLL_FREQUENCY` (+37 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh rm57l843-launchxl2:nsh && make`
