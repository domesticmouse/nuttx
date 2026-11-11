# `nrf52840-dongle/include` Component (`boards/arm/nrf52/nrf52840-dongle/include`)

## Overview
Board-level public headers (`include`) for `nrf52840-dongle` (`arm/nrf52`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_SYSTICK_CLOCK]` Hardware/board configuration macros (`BOARD_SYSTICK_CLOCK`, `BOARD_LED1`, `BOARD_NLEDS`, `BOARD_LED1_BIT`, `LED_STARTED`, `LED_HEAPALLOCATE` (+11 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh nrf52840-dongle:nsh && make`
