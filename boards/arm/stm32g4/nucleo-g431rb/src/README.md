# `nucleo-g431rb/src` Component (`boards/arm/stm32g4/nucleo-g431rb/src`)

## Overview
Board-level C implementation (`src`) for `nucleo-g431rb` (`arm/stm32g4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 10 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[nucleo-g431rb.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[nucleo-g431rb.h:stm32_pwm_setup]` Public declaration `stm32_pwm_setup()`
- `[nucleo-g431rb.h:stm32_adc_setup]` Public declaration `stm32_adc_setup()`
- `[nucleo-g431rb.h:stm32_foc_setup]` Public declaration `stm32_foc_setup()`
- `[nucleo-g431rb.h:stm32_cordic_setup]` Public declaration `stm32_cordic_setup()`
- `[nucleo-g431rb.h:GPIO_LED1]` Hardware/board configuration macros (`GPIO_LED1`, `LED_DRIVER_PATH`, `MIN_IRQBUTTON`, `MAX_IRQBUTTON`, `NUM_IRQBUTTONS`, `GPIO_BTN_USER` (+1 more))
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
- `[stm32_cordic.c:stm32_cordic_setup]` Public function `stm32_cordic_setup()`
- `[stm32_foc_ihm16m1.c:stm32_foc_setup]` Public function `stm32_foc_setup()`
- `[stm32_pwm.c:stm32_pwm_setup]` Public function `stm32_pwm_setup()`
- `[stm32_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[stm32_userleds.c:board_userled]` Public function `board_userled()`
- `[stm32_userleds.c:board_userled_all]` Public function `board_userled_all()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ADC`, `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_BOARD_STM32_IHM16M1`, `CONFIG_MATH_CORDIC` (+2 more)
- `[stm32_adc.c:stm32_adc_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[stm32_cordic.c:stm32_cordic_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_foc_ihm16m1.c:#error]` Compile-time guard: `#endif`
- `[stm32_pwm.c:stm32_pwm_setup]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[stm32_adc.c:stm32_adc_setup]` Configures or drives hardware GPIO pins
- `[stm32_adc.c:stm32_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`)
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`board_qencoder_initialize()`, `btn_lower_initialize()`, `stm32_common_initialize()`, `userled_lower_initialize()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_cordic.c:stm32_cordic_setup]` Initializes/registers kernel devices or filesystems (`cordic_register()`)
- `[stm32_foc_ihm16m1.c:stm32_foc_setup]` Initializes/registers kernel devices or filesystems (`board_ihm16m1_initialize()`)
- `[stm32_pwm.c:stm32_pwm_setup]` Initializes/registers kernel devices or filesystems (`pwm_register()`)
- `[stm32_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh nucleo-g431rb:nsh && make`
