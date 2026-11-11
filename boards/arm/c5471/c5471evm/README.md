# `c5471evm` Board Support Package (`boards/arm/c5471/c5471evm`)

## Overview
Board Support Package (BSP) blueprint for `c5471evm` (`arm` / `c5471`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `httpd`, `nettest`, `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `c5471evm` (`arm/c5471`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:C5471_CLOCK]` Hardware/board configuration macros (`C5471_CLOCK`, `LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED`, `LED_STACKCREATED`, `LED_INIRQ` (+3 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `c5471evm` (`arm/c5471`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 1 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[c5471_leds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`.
