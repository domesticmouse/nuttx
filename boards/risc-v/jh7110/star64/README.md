# `star64` Board Support Package (`boards/risc-v/jh7110/star64`)

## Overview
Board Support Package (BSP) blueprint for `star64` (`risc-v` / `jh7110`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `star64` (`risc-v/jh7110`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s). Key symbols: `[board.h:jh7110_boardinitialize]` Public declaration `jh7110_boardinitialize()`, `[board.h:LED_STARTED]` Hardware/board configuration macros (`LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED`, `LED_STACKCREATED`, `LED_INIRQ`, `LED_SIGNAL` (+3 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `star64` (`risc-v/jh7110`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 1 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[jh7110_boardinit.c:mount_ramdisk]` Public function `mount_ramdisk()`.
