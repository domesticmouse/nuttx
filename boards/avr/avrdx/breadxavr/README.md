# `breadxavr` Board Support Package (`boards/avr/avrdx/breadxavr`)

## Overview
Board Support Package (BSP) blueprint for `breadxavr` (`avr` / `avrdx`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `ws2812`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `breadxavr` (`avr/avrdx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:breadboard_buttons_e]` Type definition `breadboard_buttons_e`, `[board.h:BOARD_XTAL_FREQ]` Hardware/board configuration macros (`BOARD_XTAL_FREQ`, `BOARD_CPU_CLOCK`, `LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED`, `LED_STACKCREATED` (+4 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `breadxavr` (`avr/avrdx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[breadxavr.h:avrdx_led_initialize]` Public declaration `avrdx_led_initialize()`.
