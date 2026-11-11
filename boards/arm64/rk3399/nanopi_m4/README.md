# `nanopi_m4` Board Support Package (`boards/arm64/rk3399/nanopi_m4`)

## Overview
Board Support Package (BSP) blueprint for `nanopi_m4` (`arm64` / `rk3399`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `nanopi_m4` (`arm64/rk3399`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h]` Board header declarations `board.h`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `nanopi_m4` (`arm64/rk3399`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 2 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[nanopi_m4.h]` Board header declarations `nanopi_m4.h`.
