# `nucleo-l476rg/src` Component (`boards/arm/stm32l4/nucleo-l476rg/src`)

## Overview
Board-level C implementation (`src`) for `nucleo-l476rg` (`arm/stm32l4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 24 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[nucleo-l476rg.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[nucleo-l476rg.h:stm32_spiinitialize]` Public declaration `stm32_spiinitialize()`
- `[nucleo-l476rg.h:stm32_usbinitialize]` Public declaration `stm32_usbinitialize()`
- `[nucleo-l476rg.h:stm32_gpio_initialize]` Public declaration `stm32_gpio_initialize()`
- `[nucleo-l476rg.h:stm32_pwm_setup]` Public declaration `stm32_pwm_setup()`
- `[nucleo-l476rg.h:stm32_adc_setup]` Public declaration `stm32_adc_setup()`
- `[nucleo-l476rg.h:board_ajoy_initialize]` Public declaration `board_ajoy_initialize()`
- `[nucleo-l476rg.h:stm32_mmcsd_initialize]` Public declaration `stm32_mmcsd_initialize()`
- `[nucleo-l476rg.h:stm32_qencoder_initialize]` Public declaration `stm32_qencoder_initialize()`
- `[nucleo-l476rg.h:stm32_cc1101_initialize]` Public declaration `stm32_cc1101_initialize()`
- `[nucleo-l476rg.h:stm32_as726xinitialize]` Public declaration `stm32_as726xinitialize()`
- `[nucleo-l476rg.h:stm32_bmp180initialize]` Public declaration `stm32_bmp180initialize()`
- `[nucleo-l476rg.h:HAVE_RTC_DRIVER]` Hardware/board configuration macros (`HAVE_RTC_DRIVER`, `HAVE_MMCSD_SPI`, `HAVE_MMCSD_SDIO`, `GPIO_LD2`, `MIN_IRQBUTTON`, `MAX_IRQBUTTON` (+40 more))
- `[stm32_mpu9250.h:board_mpu9250_initialize]` Public declaration `board_mpu9250_initialize()`
- `[stm32_adc.c:stm32_adc_setup]` Public function `stm32_adc_setup()`
- `[stm32_ajoystick.c:board_ajoy_initialize]` Public function `board_ajoy_initialize()`
- `[stm32_as726x.c:stm32_as726xinitialize]` Public function `stm32_as726xinitialize()`
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_bmp180.c:stm32_bmp180initialize]` Public function `stm32_bmp180initialize()`
- `[stm32_boot.c:stm32_board_initialize]` Public function `stm32_board_initialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- *(+33 additional symbols across 24 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ADC`, `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_BOARDCTL_IOCTL`, `CONFIG_BOARDCTL_UNIQUEID` (+14 more)
- `[stm32_adc.c:stm32_adc_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_ajoystick.c:DEBUGASSERT]` Requires `g_ajoyhandler`
- `[stm32_ajoystick.c:#error]` Compile-time guard: `CONFIG_ADC is required for the Itead joystick`
- `[stm32_ajoystick.c:#error]` Compile-time guard: `CONFIG_STM32_ADC1 is required for Itead joystick`
- `[stm32_as726x.c:stm32_as726xinitialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_bmp180.c:stm32_bmp180initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_bringup.c:stm32_bringup]` Validates preconditions and returns `-ENODEV`, `-ENOMEM` on failure
- `[stm32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[stm32_cc1101.c:stm32_cc1101_initialize]` Validates preconditions and returns `-ENODEV`, `-ENOMEM` on failure
- `[stm32_gpio.c:DEBUGASSERT]` Requires `stm32gpint != NULL && stm32gpint->callback != NULL`
- `[stm32_gpio.c:DEBUGASSERT]` Requires `stm32gpio != NULL && value != NULL`

## Side Effects
- `[stm32_adc.c:stm32_adc_setup]` Configures or drives hardware GPIO pins
- `[stm32_adc.c:stm32_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`, `stm32_adc_initialize()`)
- `[stm32_ajoystick.c:board_ajoy_initialize]` Configures or drives hardware GPIO pins
- `[stm32_ajoystick.c:board_ajoy_initialize]` Initializes/registers kernel devices or filesystems (`ajoy_register()`)
- `[stm32_ajoystick.c:board_ajoy_initialize]` Modifies interrupt controller or critical-section state
- `[stm32_as726x.c:stm32_as726xinitialize]` Initializes/registers kernel devices or filesystems (`as726x_register()`, `stm32_i2cbus_initialize()`)
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_bmp180.c:stm32_bmp180initialize]` Initializes/registers kernel devices or filesystems (`bmp180_register()`, `stm32_i2cbus_initialize()`)
- `[stm32_boot.c:stm32_board_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`board_ajoy_initialize()`, `board_bmp280_initialize()`, `board_mpu9250_initialize()`, `rtc_initialize()`, `sdio_initialize()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_cc1101.c:stm32_cc1101_initialize]` Initializes/registers kernel devices or filesystems (`cc1101_register()`, `stm32_spibus_initialize()`)

## Verification
- Run: `./tools/configure.sh nucleo-l476rg:nsh && make`
