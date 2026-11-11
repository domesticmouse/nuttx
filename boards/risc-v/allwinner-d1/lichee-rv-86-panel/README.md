# `lichee-rv-86-panel` Board Support Package (`boards/risc-v/allwinner-d1/lichee-rv-86-panel`)

## Overview
Board Support Package (BSP) blueprint for `lichee-rv-86-panel` (`risc-v` / `allwinner-d1`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `lichee-rv-86-panel` (`risc-v/allwinner-d1`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:LED_STARTED]` Hardware/board configuration macros (`LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED`, `LED_STACKCREATED`, `LED_INIRQ`, `LED_SIGNAL` (+2 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `lichee-rv-86-panel` (`risc-v/allwinner-d1`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 1 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[allwinner_d1_boardinit.c:board_late_initialize]` Public function `board_late_initialize()`.
