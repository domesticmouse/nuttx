# `teensy-2.0` Board Support Package (`boards/avr/at90usb/teensy-2.0`)

## Overview
Board Support Package (BSP) blueprint for `teensy-2.0` (`avr` / `at90usb`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `hello`, `nsh`, `usbmsc`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `teensy-2.0` (`avr/at90usb`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_XTAL_FREQ]` Hardware/board configuration macros (`BOARD_XTAL_FREQ`, `BOARD_CPU_CLOCK`, `LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED`, `LED_STACKCREATED` (+4 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `teensy-2.0` (`avr/at90usb`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[teensy-20.h:at90usb_spidev_initialize]` Public declaration `at90usb_spidev_initialize()`.
