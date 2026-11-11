# `nrf5340-dk/include` Component (`boards/arm/nrf53/nrf5340-dk/include`)

## Overview
Board-level public headers (`include`) for `nrf5340-dk` (`arm/nrf53`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_SYSTICK_CLOCK]` Hardware/board configuration macros (`BOARD_SYSTICK_CLOCK`, `BOARD_OSC_XOSC32KI_INTCAP`, `BOARD_OSC_XOSC32MCAPS_CAP`, `BOARD_LED1`, `BOARD_LED2`, `BOARD_LED3` (+43 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh nrf5340-dk:adc_cpuapp && make`
