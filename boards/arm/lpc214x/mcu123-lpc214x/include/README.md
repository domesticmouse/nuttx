# `mcu123-lpc214x/include` Component (`boards/arm/lpc214x/mcu123-lpc214x/include`)

## Overview
Board-level public headers (`include`) for `mcu123-lpc214x` (`arm/lpc214x`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:LPC214X_FOSC]` Hardware/board configuration macros (`LPC214X_FOSC`, `LPC214X_PLL_M`, `LPC214X_PLL_P`, `LPC214X_APB_DIV`, `LPC214X_USBPLL_M`, `LPC214X_USBPLL_P` (+8 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh mcu123-lpc214x:nsh && make`
