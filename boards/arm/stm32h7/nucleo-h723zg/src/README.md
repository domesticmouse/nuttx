# `nucleo-h723zg/src` Component (`boards/arm/stm32h7/nucleo-h723zg/src`)

## Overview
Board-level C implementation (`src`) for `nucleo-h723zg` (`arm/stm32h7`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 14 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[nucleo-h723zg.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[nucleo-h723zg.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[nucleo-h723zg.h:stm32_adc_setup]` Public declaration `stm32_adc_setup()`
- `[nucleo-h723zg.h:stm32_gpio_initialize]` Public declaration `stm32_gpio_initialize()`
- `[nucleo-h723zg.h:stm32_usbinitialize]` Public declaration `stm32_usbinitialize()`
- `[nucleo-h723zg.h:stm32_pwm_setup]` Public declaration `stm32_pwm_setup()`
- `[nucleo-h723zg.h:stm32_oa_tc6_initialize]` Public declaration `stm32_oa_tc6_initialize()`
- `[nucleo-h723zg.h:HAVE_USBDEV]` Hardware/board configuration macros (`HAVE_USBDEV`, `HAVE_USBMONITOR`, `HAVE_MTDCONFIG`, `HAVE_PROGMEM_CHARDEV`, `PROGMEM_MTD_MINOR`, `FLASH_BASED_PARAMS` (+25 more))
- `[stm32_adc.c:stm32_adc_setup]` Public function `stm32_adc_setup()`
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- `[stm32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[stm32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[stm32_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[stm32_gpio.c:stm32_gpio_initialize]` Public function `stm32_gpio_initialize()`
- `[stm32_oa_tc6.c:stm32_oa_tc6_initialize]` Public function `stm32_oa_tc6_initialize()`
- `[stm32_pwm.c:stm32_pwm_setup]` Public function `stm32_pwm_setup()`
- `[stm32_spi.c:stm32_spidev_initialize]` Public function `stm32_spidev_initialize()`
- `[stm32_spi.c:stm32_spi1select]` Public function `stm32_spi1select()`
- *(+23 additional symbols across 14 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ADC`, `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_BOARDCTL_UNIQUEID`, `CONFIG_DEV_GPIO` (+4 more)
- `[stm32_adc.c:stm32_adc_setup]` Validates preconditions and returns `-ENODEV`, `-ENOSYS` on failure
- `[stm32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[stm32_gpio.c:DEBUGASSERT]` Requires `stm32gpint != NULL && stm32gpint->callback != NULL`
- `[stm32_gpio.c:DEBUGASSERT]` Requires `stm32gpio != NULL && value != NULL`
- `[stm32_gpio.c:DEBUGASSERT]` Requires `stm32gpio->id < BOARD_NGPIOIN`
- `[stm32_oa_tc6.c:DEBUGASSERT]` Requires `g_stm32_oa_tc6_isr != NULL && g_stm32_oa_tc6_isr_arg != NULL`
- `[stm32_pwm.c:stm32_pwm_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_spi.c:stm32_spidev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_uid.c:board_uniqueid]` Validates preconditions and returns `-EINVAL` on failure
- `[stm32_usb.c:#error]` Compile-time guard: `USB host mode is not supported`

## Side Effects
- `[stm32_adc.c:stm32_adc_setup]` Configures or drives hardware GPIO pins
- `[stm32_adc.c:stm32_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`, `stm32_adc_initialize()`)
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `stm32_spidev_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`btn_lower_initialize()`, `cdcacm_initialize()`, `stm32_common_initialize()`, `stm32_gpio_initialize()`, `stm32_oa_tc6_initialize()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_gpio.c:stm32_gpio_initialize]` Configures or drives hardware GPIO pins
- `[stm32_gpio.c:stm32_gpio_initialize]` Initializes/registers kernel devices or filesystems (`gpio_pin_register()`)
- `[stm32_oa_tc6.c:stm32_oa_tc6_initialize]` Configures or drives hardware GPIO pins
- `[stm32_oa_tc6.c:stm32_oa_tc6_initialize]` Initializes/registers kernel devices or filesystems (`oa_tc6_initialize()`, `stm32_spibus_initialize()`)
- `[stm32_pwm.c:stm32_pwm_setup]` Initializes/registers kernel devices or filesystems (`pwm_register()`)
- `[stm32_spi.c:stm32_spidev_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh nucleo-h723zg:nsh && make`
