# `stm32_tiny/src` Component (`boards/arm/stm32f1/stm32_tiny/src`)

## Overview
Board-level C implementation (`src`) for `stm32_tiny` (`arm/stm32f1`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 6 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[stm32_tiny.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[stm32_tiny.h:stm32_usbinitialize]` Public declaration `stm32_usbinitialize()`
- `[stm32_tiny.h:stm32_pwm_setup]` Public declaration `stm32_pwm_setup()`
- `[stm32_tiny.h:stm32_wlinitialize]` Public declaration `stm32_wlinitialize()`
- `[stm32_tiny.h:GPIO_LED]` Hardware/board configuration macros (`GPIO_LED`, `GPIO_USB_PULLUP`, `GPIO_NRF24L01_CS`, `STM32TINY_PWMTIMER`)
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_leds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_leds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_pwm.c:stm32_pwm_setup]` Public function `stm32_pwm_setup()`
- `[stm32_spi.c:stm32_spidev_initialize]` Public function `stm32_spidev_initialize()`
- `[stm32_spi.c:stm32_spi1select]` Public function `stm32_spi1select()`
- `[stm32_spi.c:stm32_spi1status]` Public function `stm32_spi1status()`
- `[stm32_spi.c:stm32_spi2select]` Public function `stm32_spi2select()`
- `[stm32_spi.c:stm32_spi2status]` Public function `stm32_spi2status()`
- `[stm32_usbdev.c:stm32_usbinitialize]` Public function `stm32_usbinitialize()`
- `[stm32_usbdev.c:stm32_usbpullup]` Public function `stm32_usbpullup()`
- `[stm32_usbdev.c:stm32_usbsuspend]` Public function `stm32_usbsuspend()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_PWM`
- `[stm32_tiny.h:#error]` Compile-time guard: `To use the PWM device, the timer 3 partial remap must be enabled, and th...`
- `[stm32_pwm.c:stm32_pwm_setup]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `board_nrf24l01_initialize()`, `stm32_spidev_initialize()`)
- `[stm32_leds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_pwm.c:stm32_pwm_setup]` Initializes/registers kernel devices or filesystems (`pwm_register()`)
- `[stm32_spi.c:stm32_spidev_initialize]` Configures or drives hardware GPIO pins
- `[stm32_usbdev.c:stm32_usbinitialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh stm32_tiny:nsh && make`
