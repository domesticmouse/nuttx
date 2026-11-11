# `waveshare-rp2040-lcd-1.28/src` Component (`boards/arm/rp2040/waveshare-rp2040-lcd-1.28/src`)

## Overview
Board-level C implementation (`src`) for `waveshare-rp2040-lcd-1.28` (`arm/rp2040`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[rp2040_pico.h:rp2040_bringup]` Public declaration `rp2040_bringup()`
- `[rp2040_pico.h:rp2040_dev_gpio_init]` Public declaration `rp2040_dev_gpio_init()`
- `[rp2040_boardinitialize.c:rp2040_boardearlyinitialize]` Public function `rp2040_boardearlyinitialize()`
- `[rp2040_boardinitialize.c:rp2040_boardinitialize]` Public function `rp2040_boardinitialize()`
- `[rp2040_boardinitialize.c:board_late_initialize]` Public function `board_late_initialize()`
- `[rp2040_bringup.c:rp2040_bringup]` Public function `rp2040_bringup()`
- `[rp2040_gpio.c:rp2040_dev_gpio_init]` Public function `rp2040_dev_gpio_init()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_DEV_GPIO`
- `[rp2040_gpio.c:DEBUGASSERT]` Requires `rp2040gpio != NULL && value != NULL`
- `[rp2040_gpio.c:DEBUGASSERT]` Requires `rp2040gpio->id < BOARD_NGPIOOUT`
- `[rp2040_gpio.c:DEBUGASSERT]` Requires `rp2040gpio != NULL`

## Side Effects
- `[rp2040_boardinitialize.c:rp2040_boardearlyinitialize]` Initializes/registers kernel devices or filesystems (`rp2040_common_initialize()`)
- `[rp2040_gpio.c:rp2040_dev_gpio_init]` Initializes/registers kernel devices or filesystems (`gpio_pin_register()`)

## Verification
- Run: `./tools/configure.sh waveshare-rp2040-lcd-1.28:nsh && make`
