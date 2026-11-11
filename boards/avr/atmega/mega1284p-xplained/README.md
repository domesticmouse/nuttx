# `mega1284p-xplained` Board Support Package (`boards/avr/atmega/mega1284p-xplained`)

## Overview
Board Support Package (BSP) blueprint for `mega1284p-xplained` (`avr` / `atmega`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `hello`, `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `mega1284p-xplained` (`avr/atmega`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_XTAL_FREQ]` Hardware/board configuration macros (`BOARD_XTAL_FREQ`, `BOARD_CPU_CLOCK`, `LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED`, `LED_STACKCREATED` (+4 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `mega1284p-xplained` (`avr/atmega`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 3 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[mega1284p_xplained.h:atmega_spidev_initialize]` Public declaration `atmega_spidev_initialize()`.
