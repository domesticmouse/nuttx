# `micropendous3` Board Support Package (`boards/avr/at90usb/micropendous3`)

## Overview
Board Support Package (BSP) blueprint for `micropendous3` (`avr` / `at90usb`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `hello`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `micropendous3` (`avr/at90usb`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_XTAL_FREQ]` Hardware/board configuration macros (`BOARD_XTAL_FREQ`, `BOARD_CPU_CLOCK`, `LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED`, `LED_STACKCREATED` (+4 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `micropendous3` (`avr/at90usb`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 2 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[micropendous3.h:at90usb_spidev_initialize]` Public declaration `at90usb_spidev_initialize()`.
