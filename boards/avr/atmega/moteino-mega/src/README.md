# `moteino-mega/src` Component (`boards/avr/atmega/moteino-mega/src`)

## Overview
Board-level C implementation (`src`) for `moteino-mega` (`avr/atmega`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 3 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[moteino_mega.h:atmega_spidev_initialize]` Public declaration `atmega_spidev_initialize()`
- `[moteino_mega.h:atmega_led_initialize]` Public declaration `atmega_led_initialize()`
- `[avr_boot.c:atmega_boardinitialize]` Public function `atmega_boardinitialize()`
- `[avr_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[avr_leds.c:atmega_led_initialize]` Public function `atmega_led_initialize()`
- `[avr_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[avr_leds.c:board_autoled_off]` Public function `board_autoled_off()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_LEDS`

## Side Effects
- `[avr_boot.c:atmega_boardinitialize]` Initializes/registers kernel devices or filesystems (`atmega_led_initialize()`, `atmega_spidev_initialize()`)

## Verification
- Run: `./tools/configure.sh moteino-mega:nsh && make`
