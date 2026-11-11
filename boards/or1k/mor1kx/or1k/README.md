# `or1k` Board Support Package (`boards/or1k/mor1kx/or1k`)

## Overview
Board Support Package (BSP) blueprint for `or1k` (`or1k` / `mor1kx`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `or1k` (`or1k/mor1kx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:LED_STARTED]` Hardware/board configuration macros (`LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED`, `LED_STACKCREATED`, `LED_INIRQ`, `LED_SIGNAL` (+2 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `or1k` (`or1k/mor1kx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[or1k.h:or1k_bringup]` Public declaration `or1k_bringup()`.
