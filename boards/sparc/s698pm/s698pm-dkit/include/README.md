# `s698pm-dkit/include` Component (`boards/sparc/s698pm/s698pm-dkit/include`)

## Overview
Board-level public headers (`include`) for `s698pm-dkit` (`sparc/s698pm`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_XTAL_FREQ]` Hardware/board configuration macros (`BOARD_XTAL_FREQ`, `BOARD_CPU_CLOCK`, `CHIP_NUARTS`, `BOARD_TIM1_FREQUENCY`, `BOARD_TIM2_FREQUENCY`)

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh s698pm-dkit:nsh && make`
