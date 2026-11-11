# `nucleo-f446re/src` Component (`boards/arm/stm32f4/nucleo-f446re/src`)

## Overview
Board-level C implementation (`src`) for `nucleo-f446re` (`arm/stm32f4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 14 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[nucleo-f446re.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[nucleo-f446re.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[nucleo-f446re.h:stm32_usbinitialize]` Public declaration `stm32_usbinitialize()`
- `[nucleo-f446re.h:stm32_adc_setup]` Public declaration `stm32_adc_setup()`
- `[nucleo-f446re.h:board_ajoy_initialize]` Public declaration `board_ajoy_initialize()`
- `[nucleo-f446re.h:stm32_foc_setup]` Public declaration `stm32_foc_setup()`
- `[nucleo-f446re.h:stm32_pwm_setup]` Public declaration `stm32_pwm_setup()`
- `[nucleo-f446re.h:stm32_gpio_initialize]` Public declaration `stm32_gpio_initialize()`
- `[nucleo-f446re.h:stm32_dac_setup]` Public declaration `stm32_dac_setup()`
- `[nucleo-f446re.h:HAVE_MMCSD]` Hardware/board configuration macros (`HAVE_MMCSD`, `HAVE_LCD`, `GPIO_LD2`, `MIN_IRQBUTTON`, `MAX_IRQBUTTON`, `NUM_IRQBUTTONS` (+39 more))
- `[stm32_adc.c:stm32_adc_setup]` Public function `stm32_adc_setup()`
- `[stm32_ajoystick.c:board_ajoy_initialize]` Public function `board_ajoy_initialize()`
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- `[stm32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[stm32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[stm32_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[stm32_dac.c:stm32_dac_setup]` Public function `stm32_dac_setup()`
- `[stm32_foc_ihm08m1.c:stm32_foc_setup]` Public function `stm32_foc_setup()`
- *(+18 additional symbols across 14 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ADC`, `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_BOARD_STM32_IHM08M1`, `CONFIG_DAC` (+5 more)
- `[stm32_adc.c:stm32_adc_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_ajoystick.c:DEBUGASSERT]` Requires `g_ajoyhandler`
- `[stm32_ajoystick.c:#error]` Compile-time guard: `CONFIG_ADC is required for the Itead joystick`
- `[stm32_ajoystick.c:#error]` Compile-time guard: `CONFIG_STM32_ADC1 is required for Itead joystick`
- `[stm32_bringup.c:stm32_bringup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[stm32_dac.c:stm32_dac_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_foc_ihm08m1.c:#error]` Compile-time guard: `#endif`
- `[stm32_gpio.c:DEBUGASSERT]` Requires `stm32gpint != NULL && stm32gpint->callback != NULL`
- `[stm32_gpio.c:DEBUGASSERT]` Requires `stm32gpio != NULL && value != NULL`
- `[stm32_gpio.c:DEBUGASSERT]` Requires `stm32gpio->id < BOARD_NGPIOIN`

## Side Effects
- `[stm32_adc.c:stm32_adc_setup]` Configures or drives hardware GPIO pins
- `[stm32_adc.c:stm32_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`)
- `[stm32_ajoystick.c:board_ajoy_initialize]` Configures or drives hardware GPIO pins
- `[stm32_ajoystick.c:board_ajoy_initialize]` Initializes/registers kernel devices or filesystems (`ajoy_register()`)
- `[stm32_ajoystick.c:board_ajoy_initialize]` Modifies interrupt controller or critical-section state
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `stm32_spidev_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`board_ajoy_initialize()`, `board_hall3ph_initialize()`, `board_qencoder_initialize()`, `btn_lower_initialize()`, `fb_register()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_dac.c:stm32_dac_setup]` Initializes/registers kernel devices or filesystems (`dac_register()`)
- `[stm32_foc_ihm08m1.c:stm32_foc_setup]` Initializes/registers kernel devices or filesystems (`board_ihm08m1_initialize()`)
- `[stm32_gpio.c:stm32_gpio_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh nucleo-f446re:nsh && make`
