# `lpcxpresso-lpc1768/include` Component (`boards/arm/lpc17xx_40xx/lpcxpresso-lpc1768/include`)

## Overview
Board-level public headers (`include`) for `lpcxpresso-lpc1768` (`arm/lpc17xx_40xx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `BOARD_OSCCLK_FREQUENCY`, `BOARD_RTCCLK_FREQUENCY`, `BOARD_INTRCOSC_FREQUENCY`, `LPC17_40_CCLK`, `CONFIG_LPC17_40_MAINOSC` (+38 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh lpcxpresso-lpc1768:nsh && make`
