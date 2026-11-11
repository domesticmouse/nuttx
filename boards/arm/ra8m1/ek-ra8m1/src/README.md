# `ek-ra8m1/src` Component (`boards/arm/ra8m1/ek-ra8m1/src`)

## Overview
Board-level C implementation (`src`) for `ek-ra8m1` (`arm/ra8m1`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 6 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[ek_ra8m1.h:ra8m1_bringup]` Public declaration `ra8m1_bringup()`
- `[ek_ra8m1.h:ra8m1_gpio_initialize]` Public declaration `ra8m1_gpio_initialize()`
- `[ra8m1_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[ra8m1_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[ra8m1_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[ra8m1_boot.c:ra_boardinitialize]` Public function `ra_boardinitialize()`
- `[ra8m1_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[ra8m1_bringup.c:ra8m1_bringup]` Public function `ra8m1_bringup()`
- `[ra8m1_gpio.c:ra8m1_gpio_initialize]` Public function `ra8m1_gpio_initialize()`
- `[ra8m1_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[ra8m1_userleds.c:board_userled]` Public function `board_userled()`
- `[ra8m1_userleds.c:board_userled_all]` Public function `board_userled_all()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_LEDS`, `CONFIG_DEV_GPIO`
- `[ra8m1_gpio.c:DEBUGASSERT]` Requires `ra8m1gpio != NULL && value != NULL`
- `[ra8m1_gpio.c:DEBUGASSERT]` Requires `ra8m1gpio->id < BOARD_NGPIOIN`

## Side Effects
- `[ra8m1_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[ra8m1_boot.c:ra_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[ra8m1_bringup.c:ra8m1_bringup]` Initializes/registers kernel devices or filesystems (`board_userled_initialize()`, `i2c_register()`, `ra8m1_gpio_initialize()`, `ra8m1_i2c_register()`, `ra_gpt_timer_initialize()`)
- `[ra8m1_gpio.c:ra8m1_gpio_initialize]` Configures or drives hardware GPIO pins
- `[ra8m1_gpio.c:ra8m1_gpio_initialize]` Initializes/registers kernel devices or filesystems (`gpio_pin_register()`)
- `[ra8m1_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh ek-ra8m1:nsh && make`
