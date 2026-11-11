# `elegoo-mega2560r3/src` Component (`boards/avr/atmega/elegoo-mega2560r3/src`)

## Overview
Board-level C implementation (`src`) for `elegoo-mega2560r3` (`avr/atmega`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 3 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[elegoo_mega2560r3.h]` Board header declarations `elegoo_mega2560r3.h`
- `[avr_boot.c:atmega_boardinitialize]` Public function `atmega_boardinitialize()`
- `[avr_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[avr_leds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[avr_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[avr_leds.c:board_autoled_off]` Public function `board_autoled_off()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_LEDS`

## Side Effects
- `[avr_boot.c:atmega_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)

## Verification
- Run: `./tools/configure.sh elegoo-mega2560r3:nsh && make`
