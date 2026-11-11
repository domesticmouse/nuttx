# `amber/src` Component (`boards/avr/atmega/amber/src`)

## Overview
Board-level C implementation (`src`) for `amber` (`avr/atmega`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 2 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[amber.h:atmega_spidev_initialize]` Public declaration `atmega_spidev_initialize()`
- `[amber.h:atmega_led_initialize]` Public declaration `atmega_led_initialize()`
- `[atmega_boot.c:atmega_boardinitialize]` Public function `atmega_boardinitialize()`
- `[atmega_boot.c:board_late_initialize]` Public function `board_late_initialize()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_LEDS`

## Side Effects
- `[atmega_boot.c:atmega_boardinitialize]` Initializes/registers kernel devices or filesystems (`atmega_led_initialize()`, `atmega_spidev_initialize()`)

## Verification
- Run: `./tools/configure.sh amber:hello && make`
