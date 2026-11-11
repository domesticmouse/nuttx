# `gd-xd-w515-eval/include` Component (`boards/arm/gd32w51x/gd-xd-w515-eval/include`)

## Overview
Board-level public headers (`include`) for `gd-xd-w515-eval` (`arm/gd32w51x`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_HXTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_HXTAL_FREQUENCY`, `BOARD_IRC32K_FREQUENCY`, `BOARD_SYSCLK_FREQUENCY`, `BOARD_NLEDS`, `BOARD_LED1`, `BOARD_LED2` (+50 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh gd-xd-w515-eval:nsh && make`
