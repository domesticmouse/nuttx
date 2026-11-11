# `beaglebone-black/include` Component (`boards/arm/am335x/beaglebone-black/include`)

## Overview
Board-level public headers (`include`) for `beaglebone-black` (`arm/am335x`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s).

## Interface
- `[board.h:USER_LED0]` Hardware/board configuration macros (`USER_LED0`, `USER_LED1`, `USER_LED2`, `USER_LED3`, `BOARD_NLEDS`, `BOARD_LED0_BIT` (+17 more))
- `[board_memorymap.h]` Board header declarations `board_memorymap.h`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh beaglebone-black:nsh && make`
