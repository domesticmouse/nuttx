# `z16f2800100zcog` Board Support Package (`boards/z16/z16f/z16f2800100zcog`)

## Overview
Board Support Package (BSP) blueprint for `z16f2800100zcog` (`z16` / `z16f`). Coordinates board initialization, headers, and tooling across `include, src, tools`. Includes build configurations: `nsh`, `ostest`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `z16f2800100zcog` (`z16/z16f`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `BOARD_CLKSRC`, `BOARD_SYSTEM_FREQUENCY`, `BOARD_FLOPTION0`, `BOARD_FLOPTION1`, `BOARD_FLOPTION2` (+10 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `z16f2800100zcog` (`z16/z16f`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 2 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[z16f_boot.c:z16f_board_initialize]` Public function `z16f_board_initialize()`.
- [`tools`](./tools/README.md) - Board support component `tools` for `z16f2800100zcog` (`z16/z16f`), containing 1 source/script file(s) (`dopatch.sh`). Key symbols: `[dopatch.sh]` Shell script entry point `dopatch.sh`.
