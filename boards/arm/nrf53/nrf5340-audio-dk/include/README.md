# `nrf5340-audio-dk/include` Component (`boards/arm/nrf53/nrf5340-audio-dk/include`)

## Overview
Board-level public headers (`include`) for `nrf5340-audio-dk` (`arm/nrf53`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_SYSTICK_CLOCK]` Hardware/board configuration macros (`BOARD_SYSTICK_CLOCK`, `BOARD_LED1`, `BOARD_LED2`, `BOARD_LED3`, `BOARD_NLEDS`, `BOARD_LED1_BIT` (+25 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh nrf5340-audio-dk:nsh_cpuapp && make`
