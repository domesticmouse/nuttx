# `pnev5180b/include` Component (`boards/arm/lpc17xx_40xx/pnev5180b/include`)

## Overview
Board-level public headers (`include`) for `pnev5180b` (`arm/lpc17xx_40xx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:lpc17_40_boardinitialize]` Public declaration `lpc17_40_boardinitialize()`
- `[board.h:lpc17_40_led]` Public declaration `lpc17_40_led()`
- `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `BOARD_OSCCLK_FREQUENCY`, `BOARD_RTCCLK_FREQUENCY`, `BOARD_INTRCOSC_FREQUENCY`, `LPC17_40_CCLK`, `CONFIG_LPC17_40_MAINOSC` (+22 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh pnev5180b:nsh && make`
