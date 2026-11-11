# `xiao-rp2350/src` Component (`boards/arm/rp23xx/xiao-rp2350/src`)

## Overview
Board-level C implementation (`src`) for `xiao-rp2350` (`arm/rp23xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 6 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[rp23xx_pico.h:rp23xx_bringup]` Public declaration `rp23xx_bringup()`
- `[rp23xx_pico.h:rp23xx_dev_gpio_init]` Public declaration `rp23xx_dev_gpio_init()`
- `[rp23xx_pico.h:GPIO_LED1]` Hardware/board configuration macros (`GPIO_LED1`)
- `[rp23xx_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[rp23xx_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[rp23xx_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[rp23xx_boardinitialize.c:rp23xx_boardearlyinitialize]` Public function `rp23xx_boardearlyinitialize()`
- `[rp23xx_boardinitialize.c:rp23xx_boardinitialize]` Public function `rp23xx_boardinitialize()`
- `[rp23xx_boardinitialize.c:board_late_initialize]` Public function `board_late_initialize()`
- `[rp23xx_bringup.c:rp23xx_bringup]` Public function `rp23xx_bringup()`
- `[rp23xx_gpio.c:rp23xx_dev_gpio_init]` Public function `rp23xx_dev_gpio_init()`
- `[rp23xx_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[rp23xx_userleds.c:board_userled]` Public function `board_userled()`
- `[rp23xx_userleds.c:board_userled_all]` Public function `board_userled_all()`
- `[rp23xx_userleds.c:rp23xx_led_pminitialize]` Public function `rp23xx_led_pminitialize()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_LEDS`, `CONFIG_DEV_GPIO`, `CONFIG_ETC_ROMFS`
- `[rp23xx_gpio.c:DEBUGASSERT]` Requires `rp23xxgpio != NULL && value != NULL`
- `[rp23xx_gpio.c:DEBUGASSERT]` Requires `rp23xxgpio->id < BOARD_NGPIOOUT`
- `[rp23xx_gpio.c:DEBUGASSERT]` Requires `rp23xxgpio != NULL`

## Side Effects
- `[rp23xx_boardinitialize.c:rp23xx_boardearlyinitialize]` Initializes/registers kernel devices or filesystems (`rp23xx_common_initialize()`)
- `[rp23xx_bringup.c:rp23xx_bringup]` Initializes/registers kernel devices or filesystems (`userled_lower_initialize()`)
- `[rp23xx_gpio.c:rp23xx_dev_gpio_init]` Initializes/registers kernel devices or filesystems (`gpio_pin_register()`)
- `[rp23xx_userleds.c:board_userled_initialize]` Initializes/registers kernel devices or filesystems (`pm_register()`)

## Verification
- Run: `./tools/configure.sh xiao-rp2350:nsh && make`
