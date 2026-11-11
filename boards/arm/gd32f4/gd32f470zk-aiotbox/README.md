# `gd32f470zk-aiotbox` Board Support Package (`boards/arm/gd32f4/gd32f470zk-aiotbox`)

## Overview
Board Support Package (BSP) blueprint for `gd32f470zk-aiotbox` (`arm` / `gd32f4`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `aiotboxnsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `gd32f470zk-aiotbox` (`arm/gd32f4`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:GD32_BOARD_SYSCLK_PLL_HXTAL]` Hardware/board configuration macros (`GD32_BOARD_SYSCLK_PLL_HXTAL`, `GD32_BOARD_HXTAL`, `GD32_IRC16M_VALUE`, `GD32_IRC32K_VALUE`, `GD32_HXTAL_VALUE`, `GD32_LXTAL_VALUE` (+97 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `gd32f470zk-aiotbox` (`arm/gd32f4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 16 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[gd32f470z_aiotbox.h:gd32_bringup]` Public declaration `gd32_bringup()`.
