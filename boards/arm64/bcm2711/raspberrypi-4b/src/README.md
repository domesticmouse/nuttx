# `raspberrypi-4b/src` Component (`boards/arm64/bcm2711/raspberrypi-4b/src`)

## Overview
Board-level C implementation (`src`) for `raspberrypi-4b` (`arm64/bcm2711`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 9 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[bcm2711_i2cdev.h:bcm2711_i2cdev_initialize]` Public declaration `bcm2711_i2cdev_initialize()`
- `[rpi4b.h:rpi4b_bringup]` Public declaration `rpi4b_bringup()`
- `[rpi4b.h:rpi4b_sdmmc_initialize]` Public declaration `rpi4b_sdmmc_initialize()`
- `[rpi4b.h:rpi4b_pwm_initialize]` Public declaration `rpi4b_pwm_initialize()`
- `[rpi4b.h:bcm2711_dev_gpio_init]` Public declaration `bcm2711_dev_gpio_init()`
- `[bcm2711_i2cdev.c:bcm2711_i2cdev_initialize]` Public function `bcm2711_i2cdev_initialize()`
- `[rpi4b_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[rpi4b_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[rpi4b_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[rpi4b_boardinitialize.c:bcm2711_memory_initialize]` Public function `bcm2711_memory_initialize()`
- `[rpi4b_boardinitialize.c:bcm2711_board_initialize]` Public function `bcm2711_board_initialize()`
- `[rpi4b_boardinitialize.c:board_late_initialize]` Public function `board_late_initialize()`
- `[rpi4b_bringup.c:rpi4b_bringup]` Public function `rpi4b_bringup()`
- `[rpi4b_gpio.c:bcm2711_dev_gpio_init]` Public function `bcm2711_dev_gpio_init()`
- `[rpi4b_pwm.c:rpi4b_pwm_initialize]` Public function `rpi4b_pwm_initialize()`
- `[rpi4b_sdmmc.c:rpi4b_sdmmc_initialize]` Public function `rpi4b_sdmmc_initialize()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_LEDS`, `CONFIG_BCM2711_I2C_DRIVER`, `CONFIG_BCM2711_PWM`, `CONFIG_DEV_GPIO`, `CONFIG_RPI4B_SDMMC`
- `[bcm2711_i2cdev.c:bcm2711_i2cdev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[rpi4b_gpio.c:DEBUGASSERT]` Requires `bcm2711gpio != NULL`
- `[rpi4b_gpio.c:DEBUGASSERT]` Requires `value != NULL`
- `[rpi4b_gpio.c:DEBUGASSERT]` Requires `bcm2711gpio->id < BOARD_NGPIOOUT`
- `[rpi4b_pwm.c:rpi4b_pwm_initialize]` Validates preconditions and returns `-EAGAIN` on failure
- `[rpi4b_sdmmc.c:rpi4b_sdmmc_initialize]` Validates preconditions and returns `-EIO` on failure

## Side Effects
- `[bcm2711_i2cdev.c:bcm2711_i2cdev_initialize]` Initializes/registers kernel devices or filesystems (`bcm2711_i2cbus_initialize()`, `i2c_register()`)
- `[rpi4b_boardinitialize.c:bcm2711_memory_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `nx_mount()`)
- `[rpi4b_bringup.c:rpi4b_bringup]` Initializes/registers kernel devices or filesystems (`bcm2711_i2cbus_initialize()`, `bcm2711_i2cdev_initialize()`, `bmp280_register()`, `fb_register()`, `rpi4b_pwm_initialize()`)
- `[rpi4b_gpio.c:bcm2711_dev_gpio_init]` Initializes/registers kernel devices or filesystems (`gpio_pin_register()`)
- `[rpi4b_pwm.c:rpi4b_pwm_initialize]` Initializes/registers kernel devices or filesystems (`oneshot_initialize()`, `pwm_register()`, `tone_register()`)
- `[rpi4b_sdmmc.c:rpi4b_sdmmc_initialize]` Initializes/registers kernel devices or filesystems (`bcm2711_sdio_initialize()`)

## Verification
- Run: `./tools/configure.sh raspberrypi-4b:nsh && make`
