# `nrf54lm20-dk/include` Component (`boards/arm/nrf54l/nrf54lm20-dk/include`)

## Overview
Board-level public headers (`include`) for `nrf54lm20-dk` (`arm/nrf54l`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_SYSTICK_CLOCK]` Hardware/board configuration macros (`BOARD_SYSTICK_CLOCK`, `BOARD_HFXO_CAPACITANCE`, `BOARD_LED1`, `BOARD_LED2`, `BOARD_LED3`, `BOARD_LED4` (+15 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh nrf54lm20-dk:nsh && make`
