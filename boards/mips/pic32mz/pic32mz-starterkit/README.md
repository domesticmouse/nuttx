# `pic32mz-starterkit` Board Support Package (`boards/mips/pic32mz/pic32mz-starterkit`)

## Overview
Board Support Package (BSP) blueprint for `pic32mz-starterkit` (`mips` / `pic32mz`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `pic32mz-starterkit` (`mips/pic32mz`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_POSC_FREQ]` Hardware/board configuration macros (`BOARD_POSC_FREQ`, `BOARD_SOSC_FREQ`, `BOARD_FNOSC_SPLL`, `BOARD_POSC_ECMODE`, `BOARD_POSC_SWITCH`, `BOARD_PLL_INPUT` (+45 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `pic32mz-starterkit` (`mips/pic32mz`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[pic32mz-starterkit.h:pic32mz_spidev_initialize]` Public declaration `pic32mz_spidev_initialize()`.
