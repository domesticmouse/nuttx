# `s32k344evb/include` Component (`boards/arm/s32k3xx/s32k344evb/include`)

## Overview
Board-level public headers (`include`) for `s32k344evb` (`arm/s32k3xx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `BOARD_LED0_R`, `BOARD_LED0_G`, `BOARD_LED0_B`, `BOARD_LED1_R`, `BOARD_LED1_G` (+37 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh s32k344evb:nsh && make`
