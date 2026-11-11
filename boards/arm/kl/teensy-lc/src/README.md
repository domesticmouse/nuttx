# `teensy-lc/src` Component (`boards/arm/kl/teensy-lc/src`)

## Overview
Board-level C implementation (`src`) for `teensy-lc` (`arm/kl`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[teensy-lc.h:kl_spidev_initialize]` Public declaration `kl_spidev_initialize()`
- `[teensy-lc.h:kl_pwm_setup]` Public declaration `kl_pwm_setup()`
- `[teensy-lc.h:kl_led_initialize]` Public declaration `kl_led_initialize()`
- `[teensy-lc.h:GPIO_LED]` Hardware/board configuration macros (`GPIO_LED`)
- `[kl_boardinitialize.c:kl_boardinitialize]` Public function `kl_boardinitialize()`
- `[kl_boardinitialize.c:board_late_initialize]` Public function `board_late_initialize()`
- `[kl_led.c:kl_led_initialize]` Public function `kl_led_initialize()`
- `[kl_led.c:board_autoled_on]` Public function `board_autoled_on()`
- `[kl_led.c:board_autoled_off]` Public function `board_autoled_off()`
- `[kl_pwm.c:kl_pwminitialize]` Public function `kl_pwminitialize()`
- `[kl_pwm.c:kl_pwm_setup]` Public function `kl_pwm_setup()`
- `[kl_spi.c:kl_spidev_initialize]` Public function `kl_spidev_initialize()`
- `[kl_spi.c:kl_spi0select]` Public function `kl_spi0select()`
- `[kl_spi.c:kl_spi1select]` Public function `kl_spi1select()`
- `[kl_spi.c:kl_spi0status]` Public function `kl_spi0status()`
- `[kl_spi.c:kl_spi1status]` Public function `kl_spi1status()`
- `[kl_spi.c:kl_spi0cmddata]` Public function `kl_spi0cmddata()`
- `[kl_spi.c:kl_spi1cmddata]` Public function `kl_spi1cmddata()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_LEDS`, `CONFIG_KL_SPI0`, `CONFIG_KL_SPI1`, `CONFIG_PWM`
- `[kl_pwm.c:kl_pwminitialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[kl_boardinitialize.c:kl_boardinitialize]` Configures or drives hardware GPIO pins
- `[kl_boardinitialize.c:kl_boardinitialize]` Initializes/registers kernel devices or filesystems (`kl_led_initialize()`, `kl_spidev_initialize()`)
- `[kl_led.c:kl_led_initialize]` Configures or drives hardware GPIO pins
- `[kl_pwm.c:kl_pwminitialize]` Initializes/registers kernel devices or filesystems (`pwm_register()`)

## Verification
- Run: `./tools/configure.sh teensy-lc:nsh && make`
