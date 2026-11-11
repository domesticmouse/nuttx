# `t3-gem-o1/src` Component (`boards/arm/am67/t3-gem-o1/src`)

## Overview
Board-level C implementation (`src`) for `t3-gem-o1` (`arm/am67`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 6 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[t3-gem-o1.h:am67_bringup]` Public declaration `am67_bringup()`
- `[t3-gem-o1.h:am67_spi0select]` Public declaration `am67_spi0select()`
- `[t3-gem-o1.h:am67_spi0status]` Public declaration `am67_spi0status()`
- `[t3-gem-o1.h:am67_spidev_initialize]` Public declaration `am67_spidev_initialize()`
- `[t3-gem-o1.h:am67_i2cdev_initialize]` Public declaration `am67_i2cdev_initialize()`
- `[am67_appinit.c:board_app_initialize]` Public function `board_app_initialize()`
- `[am67_appinit.c:board_late_initialize]` Public function `board_late_initialize()`
- `[am67_bringup.c:am67_bringup]` Public function `am67_bringup()`
- `[am67_i2c.c:am67_i2cdev_initialize]` Public function `am67_i2cdev_initialize()`
- `[am67_pwm.c:am67_pwmdev_initialize]` Public function `am67_pwmdev_initialize()`
- `[am67_spi.c:am67_spi0select]` Public function `am67_spi0select()`
- `[am67_spi.c:am67_spi0status]` Public function `am67_spi0status()`
- `[am67_spi.c:am67_spidev_initialize]` Public function `am67_spidev_initialize()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_AM67_EPWM0`, `CONFIG_AM67_I2C`, `CONFIG_AM67_MCSPI0`

## Side Effects
- `[am67_bringup.c:am67_bringup]` Initializes/registers kernel devices or filesystems (`am67_ecapdev_initialize()`, `am67_i2cdev_initialize()`, `am67_pwmdev_initialize()`, `am67_spidev_initialize()`, `nx_mount()`)
- `[am67_i2c.c:am67_i2cdev_initialize]` Initializes/registers kernel devices or filesystems (`am67_i2cbus_initialize()`, `i2c_register()`)
- `[am67_pwm.c:am67_pwmdev_initialize]` Initializes/registers kernel devices or filesystems (`pwm_register()`)
- `[am67_spi.c:am67_spi0select]` Configures or drives hardware GPIO pins
- `[am67_spi.c:am67_spi0select]` Initializes/registers kernel devices or filesystems (`am67_spibus_initialize()`, `spi_register()`)

## Verification
- Run: `./tools/configure.sh t3-gem-o1:nsh && make`
