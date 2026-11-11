# `open1788/include` Component (`boards/arm/lpc17xx_40xx/open1788/include`)

## Overview
Board-level public headers (`include`) for `open1788` (`arm/lpc17xx_40xx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `BOARD_OSCCLK_FREQUENCY`, `BOARD_RTCCLK_FREQUENCY`, `BOARD_INTRCOSC_FREQUENCY`, `BOARD_WDTOSC_FREQUENCY`, `LPC17_40_CCLK` (+102 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh open1788:nsh && make`
