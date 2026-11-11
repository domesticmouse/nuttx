# `z8f64200100kit` Board Support Package (`boards/z80/z8/z8f64200100kit`)

## Overview
Board Support Package (BSP) blueprint for `z8f64200100kit` (`z80` / `z8`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `ostest`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `z8f64200100kit` (`z80/z8`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:LED_STARTED]` Hardware/board configuration macros (`LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED`, `LED_STACKCREATED`, `LED_IDLE`, `LED_INIRQ` (+3 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `z8f64200100kit` (`z80/z8`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 2 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[z8_boot.c:z8_board_initialize]` Public function `z8_board_initialize()`.
