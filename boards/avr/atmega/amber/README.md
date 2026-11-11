# `amber` Board Support Package (`boards/avr/atmega/amber`)

## Overview
Board Support Package (BSP) blueprint for `amber` (`avr` / `atmega`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `hello`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `amber` (`avr/atmega`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_XTAL_FREQ]` Hardware/board configuration macros (`BOARD_XTAL_FREQ`, `BOARD_CPU_CLOCK`, `BOARD_TOSCK_CLOCK`, `LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED` (+5 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `amber` (`avr/atmega`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 2 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[amber.h:atmega_spidev_initialize]` Public declaration `atmega_spidev_initialize()`.
