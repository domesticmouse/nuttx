# `xx3823/include` Component (`boards/sparc/bm3823/xx3823/include`)

## Overview
Board-level public headers (`include`) for `xx3823` (`sparc/bm3823`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_XTAL_FREQ]` Hardware/board configuration macros (`BOARD_XTAL_FREQ`, `BOARD_CPU_CLOCK`, `BOARD_PERIPH_CLOCK`, `CHIP_NUARTS`, `BM3823_XX3823_LED1`, `BM3823_XX3823_LED2` (+14 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh xx3823:nsh && make`
