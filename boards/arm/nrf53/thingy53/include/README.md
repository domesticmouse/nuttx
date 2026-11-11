# `thingy53/include` Component (`boards/arm/nrf53/thingy53/include`)

## Overview
Board-level public headers (`include`) for `thingy53` (`arm/nrf53`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_SYSTICK_CLOCK]` Hardware/board configuration macros (`BOARD_SYSTICK_CLOCK`, `BOARD_OSC_XOSC32KI_INTCAP`, `BOARD_OSC_XOSC32MCAPS_CAP`, `BUTTON_BTN1`, `BUTTON_BTN2`, `BUTTON_BTN1_BIT` (+18 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh thingy53:composite_cpuapp && make`
