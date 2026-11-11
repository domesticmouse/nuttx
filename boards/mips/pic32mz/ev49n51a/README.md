# `ev49n51a` Board Support Package (`boards/mips/pic32mz/ev49n51a`)

## Overview
Board Support Package (BSP) blueprint for `ev49n51a` (`mips` / `pic32mz`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `bridge`, `netnsh`, `nsh`, `wlan`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `ev49n51a` (`mips/pic32mz`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_POSC_FREQ]` Hardware/board configuration macros (`BOARD_POSC_FREQ`, `BOARD_PLL_INPUT`, `BOARD_PLL_IDIV`, `BOARD_PLL_MULT`, `BOARD_PLL_ODIV`, `BOARD_CPU_CLOCK` (+29 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `ev49n51a` (`mips/pic32mz`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 6 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[ev49n51a.h:pic32mz_bringup]` Public declaration `pic32mz_bringup()`.
