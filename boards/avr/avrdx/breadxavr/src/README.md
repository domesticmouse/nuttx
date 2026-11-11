# `breadxavr/src` Component (`boards/avr/avrdx/breadxavr/src`)

## Overview
Board-level C implementation (`src`) for `breadxavr` (`avr/avrdx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[breadxavr.h:avrdx_led_initialize]` Public declaration `avrdx_led_initialize()`
- `[avr_leds.c:avrdx_led_initialize]` Public function `avrdx_led_initialize()`
- `[avr_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[avr_leds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[avrdx_boot.c:avrdx_boardinitialize]` Public function `avrdx_boardinitialize()`
- `[avrdx_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[avrdx_buttons.c:board_buttons]` Public function `board_buttons()`
- `[avrdx_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[avrdx_init.c:board_early_initialize]` Public function `board_early_initialize()`
- `[avrdx_init.c:board_late_initialize]` Public function `board_late_initialize()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_LEDS`, `CONFIG_BREADXAVR_BUTTONS_DRIVER`
- `[avrdx_buttons.c:#error]` Compile-time guard: `Button code must be initialized in board_early_initialize`

## Side Effects
- `[avrdx_boot.c:avrdx_boardinitialize]` Initializes/registers kernel devices or filesystems (`avrdx_led_initialize()`)
- `[avrdx_init.c:board_early_initialize]` Initializes/registers kernel devices or filesystems (`avrdx_ws2812_register()`, `btn_lower_initialize()`)

## Verification
- Run: `./tools/configure.sh breadxavr:nsh && make`
