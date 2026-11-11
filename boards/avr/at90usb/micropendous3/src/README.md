# `micropendous3/src` Component (`boards/avr/at90usb/micropendous3/src`)

## Overview
Board-level C implementation (`src`) for `micropendous3` (`avr/at90usb`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 2 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[micropendous3.h:at90usb_spidev_initialize]` Public declaration `at90usb_spidev_initialize()`
- `[micropendous3.h:at90usb_led_initialize]` Public declaration `at90usb_led_initialize()`
- `[at90usb_boot.c:at90usb_boardinitialize]` Public function `at90usb_boardinitialize()`
- `[at90usb_boot.c:board_late_initialize]` Public function `board_late_initialize()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_LEDS`

## Side Effects
- `[at90usb_boot.c:at90usb_boardinitialize]` Initializes/registers kernel devices or filesystems (`at90usb_led_initialize()`, `at90usb_spidev_initialize()`)

## Verification
- Run: `./tools/configure.sh micropendous3:hello && make`
