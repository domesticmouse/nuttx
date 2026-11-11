# `sure-pic32mx` Board Support Package (`boards/mips/pic32mx/sure-pic32mx`)

## Overview
Board Support Package (BSP) blueprint for `sure-pic32mx` (`mips` / `pic32mx`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `usbnsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `sure-pic32mx` (`mips/pic32mx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_POSC_FREQ]` Hardware/board configuration macros (`BOARD_POSC_FREQ`, `BOARD_SOSC_FREQ`, `BOARD_FNOSC_POSCPLL`, `BOARD_POSC_HSMODE`, `BOARD_PLL_INPUT`, `BOARD_PLL_IDIV` (+29 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `sure-pic32mx` (`mips/pic32mx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[sure-pic32mx.h:pic32mx_spidev_initialize]` Public declaration `pic32mx_spidev_initialize()`.
