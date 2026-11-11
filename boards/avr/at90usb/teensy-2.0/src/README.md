# `teensy-2.0/src` Component (`boards/avr/at90usb/teensy-2.0/src`)

## Overview
Board-level C implementation (`src`) for `teensy-2.0` (`avr/at90usb`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[teensy-20.h:at90usb_spidev_initialize]` Public declaration `at90usb_spidev_initialize()`
- `[teensy-20.h:at90usb_led_initialize]` Public declaration `at90usb_led_initialize()`
- `[at90usb_boot.c:at90usb_boardinitialize]` Public function `at90usb_boardinitialize()`
- `[at90usb_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[at90usb_leds.c:at90usb_led_initialize]` Public function `at90usb_led_initialize()`
- `[at90usb_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[at90usb_leds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[at90usb_spi.c:at90usb_spidev_initialize]` Public function `at90usb_spidev_initialize()`
- `[at90usb_spi.c:avr_spiselect]` Public function `avr_spiselect()`
- `[at90usb_spi.c:avr_spistatus]` Public function `avr_spistatus()`
- `[at90usb_usbmsc.c:board_usbmsc_initialize]` Public function `board_usbmsc_initialize()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_LEDS`, `CONFIG_AVR_SPI`, `CONFIG_USBMSC`
- `[at90usb_usbmsc.c:board_usbmsc_initialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[at90usb_boot.c:at90usb_boardinitialize]` Initializes/registers kernel devices or filesystems (`at90usb_led_initialize()`, `at90usb_spidev_initialize()`)
- `[at90usb_usbmsc.c:board_usbmsc_initialize]` Initializes/registers kernel devices or filesystems (`avr_spibus_initialize()`)

## Verification
- Run: `./tools/configure.sh teensy-2.0:nsh && make`
