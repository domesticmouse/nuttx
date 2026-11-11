# `bambino-200e/include` Component (`boards/arm/lpc43xx/bambino-200e/include`)

## Overview
Board-level public headers (`include`) for `bambino-200e` (`arm/lpc43xx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `BOARD_RTCCLK_FREQUENCY`, `BOARD_INTRCOSC_FREQUENCY`, `BOARD_PLL_MSEL`, `BOARD_PLL_NSEL`, `BOARD_PLL_PSEL` (+88 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh bambino-200e:nsh && make`
