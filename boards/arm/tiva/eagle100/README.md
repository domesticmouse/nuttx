# `eagle100` Board Support Package (`boards/arm/tiva/eagle100`)

## Overview
Board Support Package (BSP) blueprint for `eagle100` (`arm` / `tiva`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `httpd`, `nettest`, `nsh`, `nxflat`, `thttpd`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `eagle100` (`arm/tiva`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:SYSCON_RCC_XTAL]` Hardware/board configuration macros (`SYSCON_RCC_XTAL`, `XTAL_FREQUENCY`, `SYSCON_RCC_OSCSRC`, `SYSCON_RCC2_OSCSRC`, `OSCSRC_FREQUENCY`, `TIVA_SYSDIV` (+12 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `eagle100` (`arm/tiva`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[eagle100.h:lm_ssidev_initialize]` Public declaration `lm_ssidev_initialize()`.
