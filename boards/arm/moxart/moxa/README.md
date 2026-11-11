# `moxa` Board Support Package (`boards/arm/moxart/moxa`)

## Overview
Board Support Package (BSP) blueprint for `moxa` (`arm` / `moxart`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `moxa` (`arm/moxart`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:ftintc010_set_trig_mode]` Public declaration `ftintc010_set_trig_mode()`, `[board.h:ftintc010_set_trig_level]` Public declaration `ftintc010_set_trig_level()`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `moxa` (`arm/moxart`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 2 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[moxart_boot.c:board_late_initialize]` Public function `board_late_initialize()`.
