# `milkv_duos` Board Support Package (`boards/risc-v/sg2000/milkv_duos`)

## Overview
Board Support Package (BSP) blueprint for `milkv_duos` (`risc-v` / `sg2000`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `milkv_duos` (`risc-v/sg2000`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s). Key symbols: `[board.h:sg2000_boardinitialize]` Public declaration `sg2000_boardinitialize()`, `[board.h:LED_STARTED]` Hardware/board configuration macros (`LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED`, `LED_STACKCREATED`, `LED_INIRQ`, `LED_SIGNAL` (+3 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `milkv_duos` (`risc-v/sg2000`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 1 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[sg2000_boardinit.c:board_late_initialize]` Public function `board_late_initialize()`.
