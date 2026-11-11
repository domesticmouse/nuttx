# `arduino-nano-33ble/include` Component (`boards/arm/nrf52/arduino-nano-33ble/include`)

## Overview
Board-level public headers (`include`) for `arduino-nano-33ble` (`arm/nrf52`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_SYSTICK_CLOCK]` Hardware/board configuration macros (`BOARD_SYSTICK_CLOCK`, `BOARD_LED1`, `BOARD_LED2`, `BOARD_LED3`, `BOARD_LED4`, `BOARD_LED5` (+23 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh arduino-nano-33ble:nsh && make`
