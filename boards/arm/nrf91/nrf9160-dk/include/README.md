# `nrf9160-dk/include` Component (`boards/arm/nrf91/nrf9160-dk/include`)

## Overview
Board-level public headers (`include`) for `nrf9160-dk` (`arm/nrf91`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_SYSTICK_CLOCK]` Hardware/board configuration macros (`BOARD_SYSTICK_CLOCK`, `BOARD_LED1`, `BOARD_LED2`, `BOARD_LED3`, `BOARD_LED4`, `BOARD_NLEDS` (+21 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh nrf9160-dk:nsh && make`
