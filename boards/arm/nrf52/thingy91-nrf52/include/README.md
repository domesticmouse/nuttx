# `thingy91-nrf52/include` Component (`boards/arm/nrf52/thingy91-nrf52/include`)

## Overview
Board-level public headers (`include`) for `thingy91-nrf52` (`arm/nrf52`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_SYSTICK_CLOCK]` Hardware/board configuration macros (`BOARD_SYSTICK_CLOCK`, `BOARD_NLEDS`, `NUM_BUTTONS`, `BOARD_UART0_RX_PIN`, `BOARD_UART0_TX_PIN`)

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh thingy91-nrf52:usbnsh && make`
