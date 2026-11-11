# `demo9s12ne64` Board Support Package (`boards/hc/m9s12/demo9s12ne64`)

## Overview
Board Support Package (BSP) blueprint for `demo9s12ne64` (`hc` / `m9s12`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `ostest`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `demo9s12ne64` (`hc/m9s12`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:HCS12_OSCCLK]` Hardware/board configuration macros (`HCS12_OSCCLK`, `HCS12_SYNR_VALUE`, `HCS12_REFDV_VALUE`, `HCS12_PLLCLK`, `HCS12_BUSCLK`, `LED_STARTED` (+7 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `demo9s12ne64` (`hc/m9s12`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[demo9s12ne64.h:hcs12_spidev_initialize]` Public declaration `hcs12_spidev_initialize()`.
