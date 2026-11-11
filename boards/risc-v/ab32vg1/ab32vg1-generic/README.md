# `ab32vg1-generic` Board Support Package (`boards/risc-v/ab32vg1/ab32vg1-generic`)

## Overview
Board Support Package (BSP) blueprint for `ab32vg1-generic` (`risc-v` / `ab32vg1`). Coordinates board initialization, headers, and tooling across `include, src, tools`. Includes build configurations: `nsh`, `ostest`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `ab32vg1-generic` (`risc-v/ab32vg1`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_LED_RED]` Hardware/board configuration macros (`BOARD_LED_RED`, `BOARD_LED_GREEN`, `BOARD_LED_BLUE`, `BOARD_NLEDS`, `BOARD_LED_RED_BIT`, `BOARD_LED_GREEN_BIT` (+14 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `ab32vg1-generic` (`risc-v/ab32vg1`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
- [`tools`](./tools/README.md) - Board support component `tools` for `ab32vg1-generic` (`risc-v/ab32vg1`), containing 1 source/script file(s) (`ab32vg1_dl.c`). Key symbols: `[ab32vg1_dl.c:main]` Public function `main()`.
