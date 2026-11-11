# `lpc4330-xplorer/include` Component (`boards/arm/lpc43xx/lpc4330-xplorer/include`)

## Overview
Board-level public headers (`include`) for `lpc4330-xplorer` (`arm/lpc43xx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `BOARD_RTCCLK_FREQUENCY`, `BOARD_INTRCOSC_FREQUENCY`, `BOARD_PLL_MSEL`, `BOARD_PLL_NSEL`, `BOARD_PLL_PSEL` (+69 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh lpc4330-xplorer:nsh && make`
