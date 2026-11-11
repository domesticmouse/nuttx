# `flipnclick-pic32mz` Board Support Package (`boards/mips/pic32mz/flipnclick-pic32mz`)

## Overview
Board Support Package (BSP) blueprint for `flipnclick-pic32mz` (`mips` / `pic32mz`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `nxlines`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `flipnclick-pic32mz` (`mips/pic32mz`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_POSC_FREQ]` Hardware/board configuration macros (`BOARD_POSC_FREQ`, `BOARD_SOSC_FREQ`, `BOARD_FNOSC_SPLL`, `BOARD_POSC_ECMODE`, `BOARD_POSC_SWITCH`, `BOARD_PLL_INPUT` (+60 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `flipnclick-pic32mz` (`mips/pic32mz`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[flipnclick-pic32mz.h:pic32mz_spidev_initialize]` Public declaration `pic32mz_spidev_initialize()`.
