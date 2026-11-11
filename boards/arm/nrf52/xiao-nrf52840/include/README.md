# `xiao-nrf52840/include` Component (`boards/arm/nrf52/xiao-nrf52840/include`)

## Overview
Board-level public headers (`include`) for `xiao-nrf52840` (`arm/nrf52`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_SYSTICK_CLOCK]` Hardware/board configuration macros (`BOARD_SYSTICK_CLOCK`, `BOARD_LED1`, `BOARD_LED2`, `BOARD_LED3`, `BOARD_NLEDS`, `BOARD_LED1_BIT` (+12 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh xiao-nrf52840:nsh && make`
