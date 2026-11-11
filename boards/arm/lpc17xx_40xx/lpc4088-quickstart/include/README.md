# `lpc4088-quickstart/include` Component (`boards/arm/lpc17xx_40xx/lpc4088-quickstart/include`)

## Overview
Board-level public headers (`include`) for `lpc4088-quickstart` (`arm/lpc17xx_40xx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `BOARD_OSCCLK_FREQUENCY`, `BOARD_RTCCLK_FREQUENCY`, `BOARD_INTRCOSC_FREQUENCY`, `BOARD_WDTOSC_FREQUENCY`, `LPC17_40_CCLK` (+78 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh lpc4088-quickstart:nsh && make`
