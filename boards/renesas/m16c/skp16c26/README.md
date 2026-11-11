# `skp16c26` Board Support Package (`boards/renesas/m16c/skp16c26`)

## Overview
Board Support Package (BSP) blueprint for `skp16c26` (`renesas` / `m16c`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `ostest`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `skp16c26` (`renesas/m16c`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:M16C_XIN_FREQ]` Hardware/board configuration macros (`M16C_XIN_FREQ`, `M16C_DEFAULT_IPL`, `M16C_TA0_PRIO`, `LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED` (+8 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `skp16c26` (`renesas/m16c`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[skp16c26.h]` Board header declarations `skp16c26.h`.
