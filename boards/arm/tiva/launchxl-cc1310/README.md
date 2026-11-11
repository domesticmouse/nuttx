# `launchxl-cc1310` Board Support Package (`boards/arm/tiva/launchxl-cc1310`)

## Overview
Board Support Package (BSP) blueprint for `launchxl-cc1310` (`arm` / `tiva`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `launchxl-cc1310` (`arm/tiva`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:SYSCLK_FREQUENCY]` Hardware/board configuration macros (`SYSCLK_FREQUENCY`, `PCLK_FREQUENCY`, `BOARD_GLED`, `BOARD_RLED`, `BOARD_NLEDS`, `BOARD_GLED_BIT` (+16 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `launchxl-cc1310` (`arm/tiva`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[launchxl-cc1310.h:cc1310_bringup]` Public declaration `cc1310_bringup()`.
