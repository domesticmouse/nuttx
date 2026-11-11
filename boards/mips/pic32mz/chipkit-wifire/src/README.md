# `chipkit-wifire/src` Component (`boards/mips/pic32mz/chipkit-wifire/src`)

## Overview
Board-level C implementation (`src`) for `chipkit-wifire` (`mips/pic32mz`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[chipkit-wifire.h:pic32mz_spidev_initialize]` Public declaration `pic32mz_spidev_initialize()`
- `[chipkit-wifire.h:pic32mz_led_initialize]` Public declaration `pic32mz_led_initialize()`
- `[chipkit-wifire.h:pic32mz_bringup]` Public declaration `pic32mz_bringup()`
- `[chipkit-wifire.h:GPIO_LED_LD1]` Hardware/board configuration macros (`GPIO_LED_LD1`, `GPIO_LED_LD2`, `GPIO_LED_LD3`, `GPIO_LED_LD4`, `GPIO_BTN1`, `GPIO_BTN2` (+4 more))
- `[pic32mz_autoleds.c:pic32mz_led_initialize]` Public function `pic32mz_led_initialize()`
- `[pic32mz_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[pic32mz_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[pic32mz_boot.c:pic32mz_boardinitialize]` Public function `pic32mz_boardinitialize()`
- `[pic32mz_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[pic32mz_bringup.c:pic32mz_bringup]` Public function `pic32mz_bringup()`
- `[pic32mz_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[pic32mz_buttons.c:board_buttons]` Public function `board_buttons()`
- `[pic32mz_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[pic32mz_spi.c:pic32mz_spidev_initialize]` Public function `pic32mz_spidev_initialize()`
- `[pic32mz_spi.c:pic32mz_spi1select]` Public function `pic32mz_spi1select()`
- `[pic32mz_spi.c:pic32mz_spi1status]` Public function `pic32mz_spi1status()`
- `[pic32mz_spi.c:pic32mz_spi1cmddata]` Public function `pic32mz_spi1cmddata()`
- `[pic32mz_spi.c:pic32mz_spi2select]` Public function `pic32mz_spi2select()`
- `[pic32mz_spi.c:pic32mz_spi2status]` Public function `pic32mz_spi2status()`
- `[pic32mz_spi.c:pic32mz_spi2cmddata]` Public function `pic32mz_spi2cmddata()`
- `[pic32mz_spi.c:pic32mz_spi3select]` Public function `pic32mz_spi3select()`
- `[pic32mz_spi.c:pic32mz_spi3status]` Public function `pic32mz_spi3status()`
- `[pic32mz_spi.c:pic32mz_spi3cmddata]` Public function `pic32mz_spi3cmddata()`
- `[pic32mz_spi.c:pic32mz_spi4select]` Public function `pic32mz_spi4select()`
- *(+17 additional symbols across 7 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`
- `[pic32mz_buttons.c:board_button_initialize]` Validates preconditions and returns `-ENOSYS` on failure
- `[pic32mz_spi.c:pic32mz_spidev_initialize]` Validates preconditions and returns `-ENOSYS` on failure

## Side Effects
- `[pic32mz_autoleds.c:pic32mz_led_initialize]` Configures or drives hardware GPIO pins
- `[pic32mz_boot.c:pic32mz_boardinitialize]` Initializes/registers kernel devices or filesystems (`pic32mz_led_initialize()`, `pic32mz_spidev_initialize()`)
- `[pic32mz_bringup.c:pic32mz_bringup]` Initializes/registers kernel devices or filesystems (`nx_mount()`)
- `[pic32mz_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[pic32mz_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh chipkit-wifire:nsh && make`
