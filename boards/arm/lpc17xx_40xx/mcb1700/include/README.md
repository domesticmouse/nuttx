# `mcb1700/include` Component (`boards/arm/lpc17xx_40xx/mcb1700/include`)

## Overview
Board-level public headers (`include`) for `mcb1700` (`arm/lpc17xx_40xx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:lpc17_40_led]` Public declaration `lpc17_40_led()`
- `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `BOARD_OSCCLK_FREQUENCY`, `BOARD_RTCCLK_FREQUENCY`, `BOARD_INTRCOSC_FREQUENCY`, `LPC17_40_CCLK`, `CONFIG_LPC17_40_MAINOSC` (+39 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh mcb1700:nsh && make`
