# `ucans32k146/include` Component (`boards/arm/s32k1xx/ucans32k146/include`)

## Overview
Board-level public headers (`include`) for `ucans32k146` (`arm/s32k1xx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `UCANS32K146_RUN_SYSCLK_FREQUENCY`, `BOARD_LED_R`, `BOARD_LED_G`, `BOARD_LED_B`, `BOARD_NLEDS` (+37 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh ucans32k146:nsh && make`
