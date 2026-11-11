# `tms570ls31x-usb-kit/include` Component (`boards/arm/tms570/tms570ls31x-usb-kit/include`)

## Overview
Board-level public headers (`include`) for `tms570ls31x-usb-kit` (`arm/tms570`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_FCLKIN_FREQUENCY]` Hardware/board configuration macros (`BOARD_FCLKIN_FREQUENCY`, `BOARD_PLL_NR`, `BOARD_PLL_NF`, `BOARD_PLL_OD`, `BOARD_PLL_R`, `BOARD_PLL_FREQUENCY` (+34 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh tms570ls31x-usb-kit:nsh && make`
