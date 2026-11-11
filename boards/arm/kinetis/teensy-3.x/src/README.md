# `teensy-3.x/src` Component (`boards/arm/kinetis/teensy-3.x/src`)

## Overview
Board-level C implementation (`src`) for `teensy-3.x` (`arm/kinetis`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[teensy-3x.h:kinetis_spidev_initialize]` Public declaration `kinetis_spidev_initialize()`
- `[teensy-3x.h:kinetis_i2cdev_initialize]` Public declaration `kinetis_i2cdev_initialize()`
- `[teensy-3x.h:kinetis_usbinitialize]` Public declaration `kinetis_usbinitialize()`
- `[teensy-3x.h:kinetis_pwm_setup]` Public declaration `kinetis_pwm_setup()`
- `[teensy-3x.h:GPIO_LED]` Hardware/board configuration macros (`GPIO_LED`)
- `[k20_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[k20_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[k20_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[k20_boot.c:kinetis_boardinitialize]` Public function `kinetis_boardinitialize()`
- `[k20_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[k20_i2c.c:kinetis_i2cdev_initialize]` Public function `kinetis_i2cdev_initialize()`
- `[k20_pwm.c:kinetis_pwminitialize]` Public function `kinetis_pwminitialize()`
- `[k20_pwm.c:kinetis_pwm_setup]` Public function `kinetis_pwm_setup()`
- `[k20_spi.c:kinetis_spidev_initialize]` Public function `kinetis_spidev_initialize()`
- `[k20_spi.c:kinetis_spi0select]` Public function `kinetis_spi0select()`
- `[k20_spi.c:kinetis_spi0status]` Public function `kinetis_spi0status()`
- `[k20_spi.c:kinetis_spi1select]` Public function `kinetis_spi1select()`
- `[k20_spi.c:kinetis_spi1status]` Public function `kinetis_spi1status()`
- `[k20_spi.c:kinetis_spi2select]` Public function `kinetis_spi2select()`
- `[k20_spi.c:kinetis_spi2status]` Public function `kinetis_spi2status()`
- `[k20_usbdev.c:kinetis_usbinitialize]` Public function `kinetis_usbinitialize()`
- `[k20_usbdev.c:kinetis_usbpullup]` Public function `kinetis_usbpullup()`
- `[k20_usbdev.c:kinetis_usbsuspend]` Public function `kinetis_usbsuspend()`
- *(+3 additional symbols across 8 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_LEDS`, `CONFIG_KINETIS_USBOTG`, `CONFIG_PWM`
- `[k20_pwm.c:kinetis_pwminitialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[k20_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[k20_boot.c:kinetis_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `kinetis_i2cdev_initialize()`, `kinetis_spidev_initialize()`)
- `[k20_i2c.c:kinetis_i2cdev_initialize]` Initializes/registers kernel devices or filesystems (`i2c_register()`, `kinetis_i2cbus_initialize()`)
- `[k20_pwm.c:kinetis_pwminitialize]` Initializes/registers kernel devices or filesystems (`pwm_register()`)
- `[k20_usbdev.c:kinetis_usbinitialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[k20_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh teensy-3.x:nsh && make`
