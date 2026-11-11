# `ev49n51a/include` Component (`boards/mips/pic32mz/ev49n51a/include`)

## Overview
Board-level public headers (`include`) for `ev49n51a` (`mips/pic32mz`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_POSC_FREQ]` Hardware/board configuration macros (`BOARD_POSC_FREQ`, `BOARD_PLL_INPUT`, `BOARD_PLL_IDIV`, `BOARD_PLL_MULT`, `BOARD_PLL_ODIV`, `BOARD_CPU_CLOCK` (+29 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh ev49n51a:nsh && make`
