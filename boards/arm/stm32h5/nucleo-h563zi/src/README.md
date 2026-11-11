# `nucleo-h563zi/src` Component (`boards/arm/stm32h5/nucleo-h563zi/src`)

## Overview
Board-level C implementation (`src`) for `nucleo-h563zi` (`arm/stm32h5`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 13 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[nucleo-h563zi.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[nucleo-h563zi.h:stm32_spiregister]` Public declaration `stm32_spiregister()`
- `[nucleo-h563zi.h:stm32_spiinitialize]` Public declaration `stm32_spiinitialize()`
- `[nucleo-h563zi.h:stm32_adc_setup]` Public declaration `stm32_adc_setup()`
- `[nucleo-h563zi.h:stm32_dac_setup]` Public declaration `stm32_dac_setup()`
- `[nucleo-h563zi.h:stm32_dts_setup]` Public declaration `stm32_dts_setup()`
- `[nucleo-h563zi.h:stm32_pwm_setup]` Public declaration `stm32_pwm_setup()`
- `[nucleo-h563zi.h:stm32_usbhost_initialize]` Public declaration `stm32_usbhost_initialize()`
- `[nucleo-h563zi.h:HAVE_RTC_DRIVER]` Hardware/board configuration macros (`HAVE_RTC_DRIVER`, `GPIO_LD1`, `GPIO_LD2`, `GPIO_LD3`, `MIN_IRQBUTTON`, `MAX_IRQBUTTON` (+2 more))
- `[stm32_adc.c:stm32_adc_setup]` Public function `stm32_adc_setup()`
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_boot.c:stm32_board_initialize]` Public function `stm32_board_initialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- `[stm32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[stm32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[stm32_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[stm32_clockconfig.c:stm32_board_clockconfig]` Public function `stm32_board_clockconfig()`
- `[stm32_dac.c:stm32_dac_setup]` Public function `stm32_dac_setup()`
- `[stm32_dts.c:stm32_dts_setup]` Public function `stm32_dts_setup()`
- `[stm32_pwm.c:stm32_pwm_setup]` Public function `stm32_pwm_setup()`
- *(+12 additional symbols across 13 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ADC`, `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_DAC`, `CONFIG_STM32_DTS` (+3 more)
- `[stm32_adc.c:stm32_adc_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_bringup.c:stm32_bringup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[stm32_dac.c:stm32_dac_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_pwm.c:stm32_pwm_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_spi.c:stm32_spiregister]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_usb.c:stm32_usbinitialize]` Validates preconditions and returns `-ENODEV`, `-ENOEXEC` on failure

## Side Effects
- `[stm32_adc.c:stm32_adc_setup]` Configures or drives hardware GPIO pins
- `[stm32_adc.c:stm32_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`, `stm32_adc_initialize()`)
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_board_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`board_button_initialize()`, `btn_lower_initialize()`, `stm32_cap_initialize()`, `stm32_common_initialize()`, `stm32_usbhost_initialize()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_dac.c:stm32_dac_setup]` Initializes/registers kernel devices or filesystems (`dac_register()`)
- `[stm32_dts.c:stm32_dts_setup]` Initializes/registers kernel devices or filesystems (`stm32_dts_register()`)
- `[stm32_pwm.c:stm32_pwm_setup]` Initializes/registers kernel devices or filesystems (`pwm_register()`)
- `[stm32_spi.c:stm32_spiregister]` Configures or drives hardware GPIO pins
- `[stm32_spi.c:stm32_spiregister]` Initializes/registers kernel devices or filesystems (`spi_register()`, `stm32_spibus_initialize()`)
- `[stm32_usb.c:stm32_usbinitialize]` Initializes/registers kernel devices or filesystems (`stm32_usbdrdhost_initialize()`, `usbhost_cdcecm_initialize()`, `usbhost_hub_initialize()`, `usbhost_msc_initialize()`)

## Verification
- Run: `./tools/configure.sh nucleo-h563zi:nsh && make`
