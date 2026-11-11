# `gd32f450zk-aiotbox/include` Component (`boards/arm/gd32f4/gd32f450zk-aiotbox/include`)

## Overview
Board-level public headers (`include`) for `gd32f450zk-aiotbox` (`arm/gd32f4`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:GD32_BOARD_SYSCLK_PLL_HXTAL]` Hardware/board configuration macros (`GD32_BOARD_SYSCLK_PLL_HXTAL`, `GD32_BOARD_HXTAL`, `GD32_IRC16M_VALUE`, `GD32_IRC32K_VALUE`, `GD32_HXTAL_VALUE`, `GD32_LXTAL_VALUE` (+87 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh gd32f450zk-aiotbox:aiotboxnsh && make`
