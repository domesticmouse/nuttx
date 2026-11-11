# `z80sim` Board Support Package (`boards/z80/z80/z80sim`)

## Overview
Board Support Package (BSP) blueprint for `z80sim` (`z80` / `z80`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `ostest`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `z80sim` (`z80/z80`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h]` Board header declarations `board.h`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `z80sim` (`z80/z80`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[z80_irq.c:z80sim_timerisr]` Public function `z80sim_timerisr()`.
