# `launchxl-tms57004/include` Component (`boards/arm/tms570/launchxl-tms57004/include`)

## Overview
Board-level public headers (`include`) for `launchxl-tms57004` (`arm/tms570`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_FCLKIN_FREQUENCY]` Hardware/board configuration macros (`BOARD_FCLKIN_FREQUENCY`, `BOARD_PLL_NR`, `BOARD_PLL_NF`, `BOARD_PLL_OD`, `BOARD_PLL_R`, `BOARD_PLL_FREQUENCY` (+25 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh launchxl-tms57004:nsh && make`
