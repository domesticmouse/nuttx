# `nrf52832-sparkfun/include` Component (`boards/arm/nrf52/nrf52832-sparkfun/include`)

## Overview
Board-level public headers (`include`) for `nrf52832-sparkfun` (`arm/nrf52`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_SYSTICK_CLOCK]` Hardware/board configuration macros (`BOARD_SYSTICK_CLOCK`, `BOARD_LED1`, `BOARD_NLEDS`, `BOARD_LED1_BIT`, `LED_STARTED`, `LED_HEAPALLOCATE` (+11 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh nrf52832-sparkfun:nsh && make`
