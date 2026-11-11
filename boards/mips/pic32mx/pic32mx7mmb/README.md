# `pic32mx7mmb` Board Support Package (`boards/mips/pic32mx/pic32mx7mmb`)

## Overview
Board Support Package (BSP) blueprint for `pic32mx7mmb` (`mips` / `pic32mx`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `pic32mx7mmb` (`mips/pic32mx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_POSC_FREQ]` Hardware/board configuration macros (`BOARD_POSC_FREQ`, `BOARD_SOSC_FREQ`, `BOARD_FNOSC_POSCPLL`, `BOARD_POSC_XTMODE`, `BOARD_SOSC_ENABLE`, `BOARD_SOSC_IESO` (+28 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `pic32mx7mmb` (`mips/pic32mx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 9 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[pic32mx7mmb.h:pic32mx_spidev_initialize]` Public declaration `pic32mx_spidev_initialize()`.
