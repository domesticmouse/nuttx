# `arduino-mega2560` Board Support Package (`boards/avr/atmega/arduino-mega2560`)

## Overview
Board Support Package (BSP) blueprint for `arduino-mega2560` (`avr` / `atmega`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `hello`, `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `arduino-mega2560` (`avr/atmega`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_XTAL_FREQ]` Hardware/board configuration macros (`BOARD_XTAL_FREQ`, `BOARD_CPU_CLOCK`).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `arduino-mega2560` (`avr/atmega`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 3 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[arduino_mega2560.h:atmega_led_initialize]` Public declaration `atmega_led_initialize()`.
