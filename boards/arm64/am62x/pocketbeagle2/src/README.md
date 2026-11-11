# `pocketbeagle2/src` Component (`boards/arm64/am62x/pocketbeagle2/src`)

## Overview
Board-level C implementation (`src`) for `pocketbeagle2` (`arm64/am62x`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[pocketbeagle2.h:pocketbeagle2_bringup]` Public declaration `pocketbeagle2_bringup()`
- `[pocketbeagle2.h:pocketbeagle2_led_initialize]` Public declaration `pocketbeagle2_led_initialize()`
- `[pocketbeagle2.h:pocketbeagle2_gpio_initialize]` Public declaration `pocketbeagle2_gpio_initialize()`
- `[pocketbeagle2_autoleds.c:pocketbeagle2_led_initialize]` Public function `pocketbeagle2_led_initialize()`
- `[pocketbeagle2_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[pocketbeagle2_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[pocketbeagle2_boardinit.c:am62x_memory_initialize]` Public function `am62x_memory_initialize()`
- `[pocketbeagle2_boardinit.c:am62x_board_initialize]` Public function `am62x_board_initialize()`
- `[pocketbeagle2_boardinit.c:board_late_initialize]` Public function `board_late_initialize()`
- `[pocketbeagle2_bringup.c:pocketbeagle2_bringup]` Public function `pocketbeagle2_bringup()`
- `[pocketbeagle2_gpio.c:pocketbeagle2_gpio_initialize]` Public function `pocketbeagle2_gpio_initialize()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_LEDS`, `CONFIG_DEV_GPIO`
- `[pocketbeagle2_bringup.c:pocketbeagle2_bringup]` Validates preconditions and returns `-ENODEV` on failure
- `[pocketbeagle2_gpio.c:DEBUGASSERT]` Requires `pb2gpio != NULL`
- `[pocketbeagle2_gpio.c:DEBUGASSERT]` Requires `value != NULL`
- `[pocketbeagle2_gpio.c:DEBUGASSERT]` Requires `pb2gpio->id < BOARD_NGPIOOUT`

## Side Effects
- `[pocketbeagle2_boardinit.c:am62x_memory_initialize]` Initializes/registers kernel devices or filesystems (`pocketbeagle2_led_initialize()`)
- `[pocketbeagle2_bringup.c:pocketbeagle2_bringup]` Initializes/registers kernel devices or filesystems (`am62x_gpio_initialize()`, `am62x_i2cbus_initialize()`, `am62x_i2cdev_register()`, `am62x_tisci_initialize()`, `i2c_register()`)
- `[pocketbeagle2_gpio.c:pocketbeagle2_gpio_initialize]` Configures or drives hardware GPIO pins
- `[pocketbeagle2_gpio.c:pocketbeagle2_gpio_initialize]` Initializes/registers kernel devices or filesystems (`gpio_pin_register()`)

## Verification
- Run: `./tools/configure.sh pocketbeagle2:nsh && make`
