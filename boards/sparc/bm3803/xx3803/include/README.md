# `xx3803/include` Component (`boards/sparc/bm3803/xx3803/include`)

## Overview
Board-level public headers (`include`) for `xx3803` (`sparc/bm3803`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_XTAL_FREQ]` Hardware/board configuration macros (`BOARD_XTAL_FREQ`, `BOARD_CPU_CLOCK`, `CHIP_NUARTS`, `BOARD_TIM1_FREQUENCY`, `BOARD_TIM2_FREQUENCY`)

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh xx3803:nsh && make`
