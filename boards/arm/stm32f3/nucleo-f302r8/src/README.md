# `nucleo-f302r8/src` Component (`boards/arm/stm32f3/nucleo-f302r8/src`)

## Overview
Board-level C implementation (`src`) for `nucleo-f302r8` (`arm/stm32f3`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 10 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[nucleo-f302r8.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[nucleo-f302r8.h:stm32_pwm_setup]` Public declaration `stm32_pwm_setup()`
- `[nucleo-f302r8.h:stm32_foc_setup]` Public declaration `stm32_foc_setup()`
- `[nucleo-f302r8.h:stm32_adc_setup]` Public declaration `stm32_adc_setup()`
- `[nucleo-f302r8.h:GPIO_LED1]` Hardware/board configuration macros (`GPIO_LED1`, `LED_DRIVER_PATH`, `MIN_IRQBUTTON`, `MAX_IRQBUTTON`, `NUM_IRQBUTTONS`, `GPIO_BTN_USER` (+4 more))
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
- `[stm32_foc_ihm07m1.c:stm32_foc_setup]` Public function `stm32_foc_setup()`
- `[stm32_highpri.c:adc12_handler]` Public function `adc12_handler()`
- `[stm32_highpri.c:dma1ch1_handler]` Public function `dma1ch1_handler()`
- `[stm32_highpri.c:highpri_main]` Public function `highpri_main()`
- `[stm32_pwm.c:stm32_pwm_setup]` Public function `stm32_pwm_setup()`
- `[stm32_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[stm32_userleds.c:board_userled]` Public function `board_userled()`
- `[stm32_userleds.c:board_userled_all]` Public function `board_userled_all()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ADC`, `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_BOARD_STM32_IHM07M1`, `CONFIG_NUCLEOF302R8_HIGHPRI` (+1 more)
- `[stm32_adc.c:#error]` Compile-time guard: `ADC1 support must be enabled`
- `[stm32_adc.c:#error]` Compile-time guard: `ADC1 DMA support must be enabled`
- `[stm32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[stm32_foc_ihm07m1.c:#error]` Compile-time guard: `#endif`
- `[stm32_highpri.c:#error]` Compile-time guard: `CONFIG_ARCH_HIPRI_INTERRUPT is required`
- `[stm32_highpri.c:#error]` Compile-time guard: `CONFIG_ARCH_RAMVECTORS is required`
- `[stm32_pwm.c:stm32_pwm_setup]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[stm32_adc.c:stm32_adc_setup]` Configures or drives hardware GPIO pins
- `[stm32_adc.c:stm32_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`)
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`board_hall3ph_initialize()`, `board_qencoder_initialize()`, `btn_lower_initialize()`, `stm32_common_initialize()`, `userled_lower_initialize()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_foc_ihm07m1.c:stm32_foc_setup]` Initializes/registers kernel devices or filesystems (`board_ihm07m1_initialize()`)
- `[stm32_highpri.c:adc12_handler]` Configures or drives hardware GPIO pins
- `[stm32_highpri.c:adc12_handler]` Modifies interrupt controller or critical-section state
- `[stm32_pwm.c:stm32_pwm_setup]` Initializes/registers kernel devices or filesystems (`pwm_register()`)
- `[stm32_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh nucleo-f302r8:nsh && make`
