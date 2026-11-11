# `pic32mx-starterkit/src` Component (`boards/mips/pic32mx/pic32mx-starterkit/src`)

## Overview
Board-level C implementation (`src`) for `pic32mx-starterkit` (`mips/pic32mx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 6 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[pic32mx-starterkit.h:pic32mx_spidev_initialize]` Public declaration `pic32mx_spidev_initialize()`
- `[pic32mx-starterkit.h:pic32mx_led_initialize]` Public declaration `pic32mx_led_initialize()`
- `[pic32mx_boot.c:pic32mx_boardinitialize]` Public function `pic32mx_boardinitialize()`
- `[pic32mx_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[pic32mx_leds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[pic32mx_leds.c:board_userled]` Public function `board_userled()`
- `[pic32mx_leds.c:board_userled_all]` Public function `board_userled_all()`
- `[pic32mx_leds.c:pic32mx_led_initialize]` Public function `pic32mx_led_initialize()`
- `[pic32mx_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[pic32mx_leds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[pic32mx_spi.c:pic32mx_spidev_initialize]` Public function `pic32mx_spidev_initialize()`
- `[pic32mx_spi.c:pic32mx_spi1select]` Public function `pic32mx_spi1select()`
- `[pic32mx_spi.c:pic32mx_spi1status]` Public function `pic32mx_spi1status()`
- `[pic32mx_spi.c:pic32mx_spi1cmddata]` Public function `pic32mx_spi1cmddata()`
- `[pic32mx_spi.c:pic32mx_spi3select]` Public function `pic32mx_spi3select()`
- `[pic32mx_spi.c:pic32mx_spi3status]` Public function `pic32mx_spi3status()`
- `[pic32mx_spi.c:pic32mx_spi3cmddata]` Public function `pic32mx_spi3cmddata()`
- `[pic32mx_spi.c:pic32mx_spi4select]` Public function `pic32mx_spi4select()`
- `[pic32mx_spi.c:pic32mx_spi4status]` Public function `pic32mx_spi4status()`
- `[pic32mx_spi.c:pic32mx_spi4cmddata]` Public function `pic32mx_spi4cmddata()`
- `[pic32mx_usbdev.c:pic32mx_usbdevinitialize]` Public function `pic32mx_usbdevinitialize()`
- `[pic32mx_usbdev.c:pic32mx_usbpullup]` Public function `pic32mx_usbpullup()`
- `[pic32mx_usbdev.c:pic32mx_usbsuspend]` Public function `pic32mx_usbsuspend()`
- `[pic32mx_usbmsc.c:board_usbmsc_initialize]` Public function `board_usbmsc_initialize()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_PIC32MX_USBDEV`, `CONFIG_USBMSC`
- `[pic32mx_boot.c:#error]` Compile-time guard: `CONFIG_PIC32MX_USBHOST is not selected`

## Side Effects
- `[pic32mx_boot.c:pic32mx_boardinitialize]` Initializes/registers kernel devices or filesystems (`pic32_usbhost_initialize()`, `pic32mx_led_initialize()`, `pic32mx_spibus_initialize()`, `pic32mx_spidev_initialize()`, `usbhost_cdcacm_initialize()`)
- `[pic32mx_leds.c:board_userled_initialize]` Configures or drives hardware GPIO pins
- `[pic32mx_usbdev.c:pic32mx_usbdevinitialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh pic32mx-starterkit:nsh && make`
