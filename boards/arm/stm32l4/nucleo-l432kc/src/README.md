# `nucleo-l432kc/src` Component (`boards/arm/stm32l4/nucleo-l432kc/src`)

## Overview
Board-level C implementation (`src`) for `nucleo-l432kc` (`arm/stm32l4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 23 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[nucleo-l432kc.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[nucleo-l432kc.h:stm32_gpio_initialize]` Public declaration `stm32_gpio_initialize()`
- `[nucleo-l432kc.h:stm32_spiregister]` Public declaration `stm32_spiregister()`
- `[nucleo-l432kc.h:stm32_spiinitialize]` Public declaration `stm32_spiinitialize()`
- `[nucleo-l432kc.h:stm32_usbinitialize]` Public declaration `stm32_usbinitialize()`
- `[nucleo-l432kc.h:stm32_pwm_setup]` Public declaration `stm32_pwm_setup()`
- `[nucleo-l432kc.h:stm32_adc_setup]` Public declaration `stm32_adc_setup()`
- `[nucleo-l432kc.h:stm32_dac_setup]` Public declaration `stm32_dac_setup()`
- `[nucleo-l432kc.h:stm32_dac7571initialize]` Public declaration `stm32_dac7571initialize()`
- `[nucleo-l432kc.h:stm32_at45dbinitialize]` Public declaration `stm32_at45dbinitialize()`
- `[nucleo-l432kc.h:stm32_w25initialize]` Public declaration `stm32_w25initialize()`
- `[nucleo-l432kc.h:stm32_ina226initialize]` Public declaration `stm32_ina226initialize()`
- `[nucleo-l432kc.h:stm32_ina219initialize]` Public declaration `stm32_ina219initialize()`
- `[nucleo-l432kc.h:stm32_zerocross_initialize]` Public declaration `stm32_zerocross_initialize()`
- `[nucleo-l432kc.h:stm32_qencoder_initialize]` Public declaration `stm32_qencoder_initialize()`
- `[nucleo-l432kc.h:HAVE_RTC_DRIVER]` Hardware/board configuration macros (`HAVE_RTC_DRIVER`, `HAVE_AT45DB`, `HAVE_W25`, `GPIO_LD3`, `LED_DRIVER_PATH`, `AT45DB_SPI1_CS` (+8 more))
- `[stm32_adc.c:stm32_adc_setup]` Public function `stm32_adc_setup()`
- `[stm32_at45db.c:stm32_at45dbinitialize]` Public function `stm32_at45dbinitialize()`
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_boot.c:stm32_board_initialize]` Public function `stm32_board_initialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- *(+31 additional symbols across 23 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_BOARDCTL_IOCTL`, `CONFIG_BOARDCTL_UNIQUEID`, `CONFIG_DAC7571` (+14 more)
- `[stm32_adc.c:stm32_adc_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_at45db.c:#error]` Compile-time guard: `AT45DB driver requires CONFIG_STM32_SPI1 to be enabled`
- `[stm32_bringup.c:stm32_bringup]` Validates preconditions and returns `-ENOMEM` on failure
- `[stm32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[stm32_dac.c:stm32_dac_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_dac7571.c:stm32_dac7571initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_dac_wgen.c:DEBUGASSERT]` Requires `x >= 0 && x <= 2 * M_PI`
- `[stm32_dac_wgen.c:#error]` Compile-time guard: `CONFIG_DAC is required`
- `[stm32_dac_wgen.c:#error]` Compile-time guard: `CONFIG_STM32_DAC1 is required`
- `[stm32_gpio.c:DEBUGASSERT]` Requires `stm32gpio != NULL && value != NULL`
- `[stm32_gpio.c:DEBUGASSERT]` Requires `stm32gpio->id < BOARD_NGPIOIN`

## Side Effects
- `[stm32_adc.c:stm32_adc_setup]` Configures or drives hardware GPIO pins
- `[stm32_adc.c:stm32_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`, `stm32_adc_initialize()`)
- `[stm32_at45db.c:stm32_at45dbinitialize]` Initializes/registers kernel devices or filesystems (`at45db_initialize()`, `nx_mount()`, `nxffs_initialize()`, `stm32_spibus_initialize()`)
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_board_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`rtc_initialize()`, `stm32_common_initialize()`, `stm32_gpio_initialize()`, `stm32_qencoder_initialize()`, `stm32_zerocross_initialize()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_dac.c:stm32_dac_setup]` Initializes/registers kernel devices or filesystems (`dac_register()`)
- `[stm32_dac7571.c:stm32_dac7571initialize]` Configures or drives hardware GPIO pins
- `[stm32_dac7571.c:stm32_dac7571initialize]` Initializes/registers kernel devices or filesystems (`dac7571_initialize()`, `dac_register()`, `stm32_i2cbus_initialize()`)
- `[stm32_gpio.c:stm32_gpio_initialize]` Configures or drives hardware GPIO pins
- `[stm32_gpio.c:stm32_gpio_initialize]` Initializes/registers kernel devices or filesystems (`gpio_pin_register()`)

## Verification
- Run: `./tools/configure.sh nucleo-l432kc:nsh && make`
