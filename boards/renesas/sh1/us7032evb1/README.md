# `us7032evb1` Board Support Package (`boards/renesas/sh1/us7032evb1`)

## Overview
Board Support Package (BSP) blueprint for `us7032evb1` (`renesas` / `sh1`). Coordinates board initialization, headers, and tooling across `include, shterm, src`. Includes build configurations: `nsh`, `ostest`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `us7032evb1` (`renesas/sh1`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:SH1_CLOCK]` Hardware/board configuration macros (`SH1_CLOCK`, `LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED`, `LED_STACKCREATED`, `LED_INIRQ` (+3 more)).
- [`shterm`](./shterm/README.md) - Board support component `shterm` for `us7032evb1` (`renesas/sh1`), containing 1 source/script file(s) (`shterm.c`). Key symbols: `[shterm.c:main]` Public function `main()`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `us7032evb1` (`renesas/sh1`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 1 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[sh1_leds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`.
