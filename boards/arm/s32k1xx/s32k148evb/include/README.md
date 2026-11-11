# `s32k148evb/include` Component (`boards/arm/s32k1xx/s32k148evb/include`)

## Overview
Board-level public headers (`include`) for `s32k148evb` (`arm/s32k1xx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `S32K148EVB_RUN_SYSCLK_FREQUENCY`, `BOARD_LED_R`, `BOARD_LED_G`, `BOARD_LED_B`, `BOARD_NLEDS` (+24 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh s32k148evb:nsh && make`
