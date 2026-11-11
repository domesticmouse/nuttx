# `xx3803` Board Support Package (`boards/sparc/bm3803/xx3803`)

## Overview
Board Support Package (BSP) blueprint for `xx3803` (`sparc` / `bm3803`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `xx3803` (`sparc/bm3803`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_XTAL_FREQ]` Hardware/board configuration macros (`BOARD_XTAL_FREQ`, `BOARD_CPU_CLOCK`, `CHIP_NUARTS`, `BOARD_TIM1_FREQUENCY`, `BOARD_TIM2_FREQUENCY`).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `xx3803` (`sparc/bm3803`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[xx3803.h:bm3803_led_initialize]` Public declaration `bm3803_led_initialize()`.
