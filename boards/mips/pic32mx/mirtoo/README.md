# `mirtoo` Board Support Package (`boards/mips/pic32mx/mirtoo`)

## Overview
Board Support Package (BSP) blueprint for `mirtoo` (`mips` / `pic32mx`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `nxffs`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `mirtoo` (`mips/pic32mx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_FRC_FREQ]` Hardware/board configuration macros (`BOARD_FRC_FREQ`, `BOARD_FNOSC_FRCPLL`, `BOARD_POSC_DISABLED`, `BOARD_PLL_INPUT`, `BOARD_PLL_IDIV`, `BOARD_PLL_MULT` (+22 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `mirtoo` (`mips/pic32mx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[mirtoo.h:pic32mx_spi2initialize]` Public declaration `pic32mx_spi2initialize()`.
