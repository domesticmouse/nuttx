# `mcb1700/src` Component (`boards/arm/lpc17xx_40xx/mcb1700/src`)

## Overview
Board-level C implementation (`src`) for `mcb1700` (`arm/lpc17xx_40xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[mcb1700.h:mcb1700_bringup]` Public declaration `mcb1700_bringup()`
- `[mcb1700.h:mcb1700_sspdev_initialize]` Public declaration `mcb1700_sspdev_initialize()`
- `[mcb1700.h:mcb1700_pwm_setup]` Public declaration `mcb1700_pwm_setup()`
- `[mcb1700.h:mcb1700_adc_setup]` Public declaration `mcb1700_adc_setup()`
- `[mcb1700.h:MCB1700_LED1]` Hardware/board configuration macros (`MCB1700_LED1`, `MCB1700_LED1_OFF`, `MCB1700_LED1_ON`, `MCB1700_LED2`, `MCB1700_LED2_OFF`, `MCB1700_LED2_ON` (+7 more))
- `[lpc17_40_adc.c:mcb1700_adc_setup]` Public function `mcb1700_adc_setup()`
- `[lpc17_40_boot.c:lpc17_40_boardinitialize]` Public function `lpc17_40_boardinitialize()`
- `[lpc17_40_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[lpc17_40_bringup.c:mcb1700_bringup]` Public function `mcb1700_bringup()`
- `[lpc17_40_dac.c:dac_devinit]` Public function `dac_devinit()`
- `[lpc17_40_leds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[lpc17_40_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[lpc17_40_leds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[lpc17_40_leds.c:lpc17_40_led]` Public function `lpc17_40_led()`
- `[lpc17_40_pwm.c:lpc17_40_pwminitialize]` Public function `lpc17_40_pwminitialize()`
- `[lpc17_40_pwm.c:lpc17_40_mcpwminitialize]` Public function `lpc17_40_mcpwminitialize()`
- `[lpc17_40_pwm.c:lpc17_40_timerinitialize]` Public function `lpc17_40_timerinitialize()`
- `[lpc17_40_pwm.c:mcb1700_pwm_setup]` Public function `mcb1700_pwm_setup()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ADC`, `CONFIG_PWM`, `CONFIG_USBMSC`
- `[lpc17_40_adc.c:mcb1700_adc_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[lpc17_40_bringup.c:#error]` Compile-time guard: `CONFIG_LPC17_40_USBHOST is not selected`
- `[lpc17_40_dac.c:dac_devinit]` Validates preconditions and returns `-ENODEV` on failure
- `[lpc17_40_pwm.c:lpc17_40_pwminitialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[lpc17_40_adc.c:mcb1700_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`)
- `[lpc17_40_boot.c:lpc17_40_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[lpc17_40_bringup.c:mcb1700_bringup]` Configures or drives hardware GPIO pins
- `[lpc17_40_bringup.c:mcb1700_bringup]` Initializes/registers kernel devices or filesystems (`lpc17_40_sspbus_initialize()`, `lpc17_40_usbhost_initialize()`, `nx_mount()`, `usbhost_cdcacm_initialize()`, `usbhost_hub_initialize()`)
- `[lpc17_40_dac.c:dac_devinit]` Initializes/registers kernel devices or filesystems (`dac_register()`)
- `[lpc17_40_leds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[lpc17_40_pwm.c:lpc17_40_pwminitialize]` Initializes/registers kernel devices or filesystems (`pwm_register()`)

## Verification
- Run: `./tools/configure.sh mcb1700:nsh && make`
