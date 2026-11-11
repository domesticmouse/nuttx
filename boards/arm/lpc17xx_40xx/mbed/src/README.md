# `mbed/src` Component (`boards/arm/lpc17xx_40xx/mbed/src`)

## Overview
Board-level C implementation (`src`) for `mbed` (`arm/lpc17xx_40xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[mbed.h:mbed_sspdev_initialize]` Public declaration `mbed_sspdev_initialize()`
- `[mbed.h:mbed_pwm_setup]` Public declaration `mbed_pwm_setup()`
- `[mbed.h:mbed_adc_setup]` Public declaration `mbed_adc_setup()`
- `[mbed.h:MBED_LED1]` Hardware/board configuration macros (`MBED_LED1`, `MBED_LED2`, `MBED_LED3`, `MBED_LED4`, `MBED_HEARTBEAT`, `MBED_NLEDS` (+4 more))
- `[lpc17_40_adc.c:mbed_adc_setup]` Public function `mbed_adc_setup()`
- `[lpc17_40_boot.c:lpc17_40_boardinitialize]` Public function `lpc17_40_boardinitialize()`
- `[lpc17_40_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[lpc17_40_dac.c:dac_devinit]` Public function `dac_devinit()`
- `[lpc17_40_leds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[lpc17_40_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[lpc17_40_leds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[lpc17_40_leds.c:lpc17_40_led]` Public function `lpc17_40_led()`
- `[lpc17_40_pwm.c:lpc17_40_pwminitialize]` Public function `lpc17_40_pwminitialize()`
- `[lpc17_40_pwm.c:lpc17_40_mcpwminitialize]` Public function `lpc17_40_mcpwminitialize()`
- `[lpc17_40_pwm.c:lpc17_40_timerinitialize]` Public function `lpc17_40_timerinitialize()`
- `[lpc17_40_pwm.c:mbed_pwm_setup]` Public function `mbed_pwm_setup()`
- `[lpc17_40_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[lpc17_40_userleds.c:board_userled]` Public function `board_userled()`
- `[lpc17_40_userleds.c:board_userled_all]` Public function `board_userled_all()`
- `[lpc17_40_userleds.c:lpc17_40_led_pminitialize]` Public function `lpc17_40_led_pminitialize()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ADC`, `CONFIG_ARCH_LEDS`, `CONFIG_PWM`, `CONFIG_USBMSC`, `CONFIG_USERLED`
- `[lpc17_40_adc.c:mbed_adc_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[lpc17_40_boot.c:#error]` Compile-time guard: `Unrecognized board`
- `[lpc17_40_dac.c:dac_devinit]` Validates preconditions and returns `-ENODEV` on failure
- `[lpc17_40_pwm.c:lpc17_40_pwminitialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[lpc17_40_adc.c:mbed_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`)
- `[lpc17_40_boot.c:lpc17_40_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `userled_lower_initialize()`)
- `[lpc17_40_dac.c:dac_devinit]` Initializes/registers kernel devices or filesystems (`dac_register()`)
- `[lpc17_40_leds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[lpc17_40_pwm.c:lpc17_40_pwminitialize]` Initializes/registers kernel devices or filesystems (`pwm_register()`)
- `[lpc17_40_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins
- `[lpc17_40_userleds.c:board_userled_initialize]` Initializes/registers kernel devices or filesystems (`pm_register()`)

## Verification
- Run: `./tools/configure.sh mbed:nsh && make`
