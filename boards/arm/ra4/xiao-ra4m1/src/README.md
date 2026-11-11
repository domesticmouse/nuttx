# `xiao-ra4m1/src` Component (`boards/arm/ra4/xiao-ra4m1/src`)

## Overview
Board-level C implementation (`src`) for `xiao-ra4m1` (`arm/ra4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 6 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[xiao-ra4m1.h:ra4m1_bringup]` Public declaration `ra4m1_bringup()`
- `[xiao-ra4m1.h:ra_gpio_initialize]` Public declaration `ra_gpio_initialize()`
- `[ra4m1_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[ra4m1_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[ra4m1_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[ra4m1_boot.c:ra_boardinitialize]` Public function `ra_boardinitialize()`
- `[ra4m1_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[ra4m1_bringup.c:ra4m1_bringup]` Public function `ra4m1_bringup()`
- `[ra4m1_gpio.c:ra_gpio_initialize]` Public function `ra_gpio_initialize()`
- `[ra4m1_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[ra4m1_userleds.c:board_userled]` Public function `board_userled()`
- `[ra4m1_userleds.c:board_userled_all]` Public function `board_userled_all()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_LEDS`, `CONFIG_DEV_GPIO`
- `[ra4m1_gpio.c:DEBUGASSERT]` Requires `ragpio != NULL && value != NULL`
- `[ra4m1_gpio.c:DEBUGASSERT]` Requires `ragpio->id < BOARD_NGPIOIN`

## Side Effects
- `[ra4m1_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[ra4m1_boot.c:ra_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[ra4m1_bringup.c:ra4m1_bringup]` Initializes/registers kernel devices or filesystems (`board_userled_initialize()`, `ra_gpio_initialize()`, `userled_lower_initialize()`)
- `[ra4m1_gpio.c:ra_gpio_initialize]` Configures or drives hardware GPIO pins
- `[ra4m1_gpio.c:ra_gpio_initialize]` Initializes/registers kernel devices or filesystems (`gpio_pin_register()`)
- `[ra4m1_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh xiao-ra4m1:nsh && make`
