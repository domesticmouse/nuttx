# `pcduino-a10/include` Component (`boards/arm/a1x/pcduino-a10/include`)

## Overview
Board-level public headers (`include`) for `pcduino-a10` (`arm/a1x`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s).

## Interface
- `[board.h:BOARD_LED1]` Hardware/board configuration macros (`BOARD_LED1`, `BOARD_LED3`, `BOARD_LED4`, `BOARD_NLEDS`, `BOARD_LED1_BIT`, `BOARD_LED3_BIT` (+20 more))
- `[board_memorymap.h]` Board header declarations `board_memorymap.h`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh pcduino-a10:nsh && make`
