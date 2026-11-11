# `nrf52832-dk/include` Component (`boards/arm/nrf52/nrf52832-dk/include`)

## Overview
Board-level public headers (`include`) for `nrf52832-dk` (`arm/nrf52`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_SYSTICK_CLOCK]` Hardware/board configuration macros (`BOARD_SYSTICK_CLOCK`, `BOARD_LED1`, `BOARD_LED2`, `BOARD_LED3`, `BOARD_LED4`, `BOARD_NLEDS` (+26 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh nrf52832-dk:nsh && make`
