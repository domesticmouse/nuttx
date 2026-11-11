# `nucleo-g431kb/src` Component (`boards/arm/stm32g4/nucleo-g431kb/src`)

## Overview
Board-level C implementation (`src`) for `nucleo-g431kb` (`arm/stm32g4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[nucleo-g431kb.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[nucleo-g431kb.h:stm32_pwm_setup]` Public declaration `stm32_pwm_setup()`
- `[nucleo-g431kb.h:stm32_comp_setup]` Public declaration `stm32_comp_setup()`
- `[nucleo-g431kb.h:stm32_dac_setup]` Public declaration `stm32_dac_setup()`
- `[nucleo-g431kb.h:GPIO_LED1]` Hardware/board configuration macros (`GPIO_LED1`, `LED_DRIVER_PATH`, `NUCLEOG431KB_PWM_TIMER`, `NUCLEOG431KB_PWM_PATH`)
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- `[stm32_comp.c:stm32_comp_setup]` Public function `stm32_comp_setup()`
- `[stm32_dac.c:stm32_dac_setup]` Public function `stm32_dac_setup()`
- `[stm32_pwm.c:stm32_pwm_setup]` Public function `stm32_pwm_setup()`
- `[stm32_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[stm32_userleds.c:board_userled]` Public function `board_userled()`
- `[stm32_userleds.c:board_userled_all]` Public function `board_userled_all()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_LEDS`, `CONFIG_PWM`, `CONFIG_STM32_COMP`, `CONFIG_STM32_DAC`
- `[stm32_comp.c:#error]` Compile-time guard: `Currently only one COMP device supported`
- `[stm32_dac.c:stm32_dac_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_pwm.c:stm32_pwm_setup]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`stm32_common_initialize()`, `userled_lower_initialize()`)
- `[stm32_comp.c:stm32_comp_setup]` Initializes/registers kernel devices or filesystems (`comp_register()`)
- `[stm32_dac.c:stm32_dac_setup]` Initializes/registers kernel devices or filesystems (`dac_register()`)
- `[stm32_pwm.c:stm32_pwm_setup]` Initializes/registers kernel devices or filesystems (`pwm_register()`)
- `[stm32_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh nucleo-g431kb:nsh && make`
