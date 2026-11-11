# `ab32vg1-generic/include` Component (`boards/risc-v/ab32vg1/ab32vg1-generic/include`)

## Overview
Board-level public headers (`include`) for `ab32vg1-generic` (`risc-v/ab32vg1`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_LED_RED]` Hardware/board configuration macros (`BOARD_LED_RED`, `BOARD_LED_GREEN`, `BOARD_LED_BLUE`, `BOARD_NLEDS`, `BOARD_LED_RED_BIT`, `BOARD_LED_GREEN_BIT` (+14 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh ab32vg1-generic:nsh && make`
