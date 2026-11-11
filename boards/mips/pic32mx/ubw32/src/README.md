# `ubw32/src` Component (`boards/mips/pic32mx/ubw32/src`)

## Overview
Board-level C implementation (`src`) for `ubw32` (`mips/pic32mx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[ubw32.h:pic32mx_spidev_initialize]` Public declaration `pic32mx_spidev_initialize()`
- `[ubw32.h:pic32mx_led_initialize]` Public declaration `pic32mx_led_initialize()`
- `[pic32_boot.c:pic32mx_boardinitialize]` Public function `pic32mx_boardinitialize()`
- `[pic32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[pic32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[pic32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[pic32_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[pic32_leds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[pic32_leds.c:board_userled]` Public function `board_userled()`
- `[pic32_leds.c:board_userled_all]` Public function `board_userled_all()`
- `[pic32_leds.c:pic32mx_led_initialize]` Public function `pic32mx_led_initialize()`
- `[pic32_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[pic32_leds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[pic32_usbdev.c:pic32mx_usbdevinitialize]` Public function `pic32mx_usbdevinitialize()`
- `[pic32_usbdev.c:pic32mx_usbpullup]` Public function `pic32mx_usbpullup()`
- `[pic32_usbdev.c:pic32mx_usbsuspend]` Public function `pic32mx_usbsuspend()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_PIC32MX_USBDEV`
- `[pic32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure

## Side Effects
- `[pic32_boot.c:pic32mx_boardinitialize]` Initializes/registers kernel devices or filesystems (`pic32mx_led_initialize()`, `pic32mx_spidev_initialize()`)
- `[pic32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[pic32_leds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh ubw32:nsh && make`
