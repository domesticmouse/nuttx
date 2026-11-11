# `xx3823` Board Support Package (`boards/sparc/bm3823/xx3823`)

## Overview
Board Support Package (BSP) blueprint for `xx3823` (`sparc` / `bm3823`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `xx3823` (`sparc/bm3823`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_XTAL_FREQ]` Hardware/board configuration macros (`BOARD_XTAL_FREQ`, `BOARD_CPU_CLOCK`, `BOARD_PERIPH_CLOCK`, `CHIP_NUARTS`, `BM3823_XX3823_LED1`, `BM3823_XX3823_LED2` (+14 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `xx3823` (`sparc/bm3823`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[xx3823.h:bm3823_led_initialize]` Public declaration `bm3823_led_initialize()`.
