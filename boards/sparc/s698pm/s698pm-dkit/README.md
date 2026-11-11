# `s698pm-dkit` Board Support Package (`boards/sparc/s698pm/s698pm-dkit`)

## Overview
Board Support Package (BSP) blueprint for `s698pm-dkit` (`sparc` / `s698pm`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `smp`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `s698pm-dkit` (`sparc/s698pm`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_XTAL_FREQ]` Hardware/board configuration macros (`BOARD_XTAL_FREQ`, `BOARD_CPU_CLOCK`, `CHIP_NUARTS`, `BOARD_TIM1_FREQUENCY`, `BOARD_TIM2_FREQUENCY`).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `s698pm-dkit` (`sparc/s698pm`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 3 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[s698pm-dkit.h:s698pm_led_initialize]` Public declaration `s698pm_led_initialize()`.
