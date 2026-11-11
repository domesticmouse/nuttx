# `olimex-lpc1766stk/include` Component (`boards/arm/lpc17xx_40xx/olimex-lpc1766stk/include`)

## Overview
Board-level public headers (`include`) for `olimex-lpc1766stk` (`arm/lpc17xx_40xx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `BOARD_OSCCLK_FREQUENCY`, `BOARD_RTCCLK_FREQUENCY`, `BOARD_INTRCOSC_FREQUENCY`, `LPC17_40_CCLK`, `CONFIG_LPC17_40_MAINOSC` (+67 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh olimex-lpc1766stk:nsh && make`
