# `thingy52/include` Component (`boards/arm/nrf52/thingy52/include`)

## Overview
Board-level public headers (`include`) for `thingy52` (`arm/nrf52`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_SYSTICK_CLOCK]` Hardware/board configuration macros (`BOARD_SYSTICK_CLOCK`, `BUTTON_BTN1`, `NUM_BUTTONS`, `BUTTON_BTN1_BIT`, `BOARD_UART0_RX_PIN`, `BOARD_UART0_TX_PIN` (+3 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh thingy52:nsh && make`
