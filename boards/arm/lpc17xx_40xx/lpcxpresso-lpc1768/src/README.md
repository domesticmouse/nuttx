# `lpcxpresso-lpc1768/src` Component (`boards/arm/lpc17xx_40xx/lpcxpresso-lpc1768/src`)

## Overview
Board-level C implementation (`src`) for `lpcxpresso-lpc1768` (`arm/lpc17xx_40xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 9 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[lpcxpresso-lpc1768.h:lpcxpresso_sspdev_initialize]` Public declaration `lpcxpresso_sspdev_initialize()`
- `[lpcxpresso-lpc1768.h:lpcexpresso_pwm_setup]` Public declaration `lpcexpresso_pwm_setup()`
- `[lpcxpresso-lpc1768.h:lpcxpresso_adc_setup]` Public declaration `lpcxpresso_adc_setup()`
- `[lpcxpresso-lpc1768.h:LPCXPRESSO_I2C1_EPROM_SDA]` Hardware/board configuration macros (`LPCXPRESSO_I2C1_EPROM_SDA`, `LPCXPRESSO_I2C1_EPROM_SDL`, `LPCXPRESSO_LED`, `LPCXPRESSO_USB_PULLUP`, `LPCXPRESSO_SD_CS`, `LPCXPRESSO_SD_CD` (+5 more))
- `[lpc17_40_adc.c:lpcxpresso_adc_setup]` Public function `lpcxpresso_adc_setup()`
- `[lpc17_40_boot.c:lpc17_40_boardinitialize]` Public function `lpc17_40_boardinitialize()`
- `[lpc17_40_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[lpc17_40_dac.c:dac_devinit]` Public function `dac_devinit()`
- `[lpc17_40_leds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[lpc17_40_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[lpc17_40_leds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[lpc17_40_oled.c:board_graphics_setup]` Public function `board_graphics_setup()`
- `[lpc17_40_oled.c:lpc17_40_ssp1cmddata]` Public function `lpc17_40_ssp1cmddata()`
- `[lpc17_40_oled.c:ug_power]` Public function `ug_power()`
- `[lpc17_40_pwm.c:lpc17_40_pwminitialize]` Public function `lpc17_40_pwminitialize()`
- `[lpc17_40_pwm.c:lpc17_40_mcpwminitialize]` Public function `lpc17_40_mcpwminitialize()`
- `[lpc17_40_pwm.c:lpc17_40_timerinitialize]` Public function `lpc17_40_timerinitialize()`
- `[lpc17_40_pwm.c:lpcexpresso_pwm_setup]` Public function `lpcexpresso_pwm_setup()`
- `[lpc17_40_ssp.c:lpcxpresso_sspdev_initialize]` Public function `lpcxpresso_sspdev_initialize()`
- `[lpc17_40_ssp.c:lpc17_40_ssp0select]` Public function `lpc17_40_ssp0select()`
- `[lpc17_40_ssp.c:lpc17_40_ssp0status]` Public function `lpc17_40_ssp0status()`
- `[lpc17_40_ssp.c:lpc17_40_ssp1select]` Public function `lpc17_40_ssp1select()`
- `[lpc17_40_ssp.c:lpc17_40_ssp1status]` Public function `lpc17_40_ssp1status()`
- *(+1 additional symbols across 9 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ADC`, `CONFIG_NX_LCDDRIVER`, `CONFIG_PWM`, `CONFIG_USBMSC`
- `[lpc17_40_adc.c:lpcxpresso_adc_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[lpc17_40_dac.c:dac_devinit]` Validates preconditions and returns `-ENODEV` on failure
- `[lpc17_40_oled.c:#error]` Compile-time guard: `The OLED driver requires CONFIG_LPC17_40_SSP1 in the configuration`
- `[lpc17_40_oled.c:#error]` Compile-time guard: `This logic requires CONFIG_UG9664HSWAG01_POWER in the configuration`
- `[lpc17_40_pwm.c:lpc17_40_pwminitialize]` Validates preconditions and returns `-ENODEV` on failure
- `[lpc17_40_usbmsc.c:#error]` Compile-time guard: `Unrecognized LPC17xx/LPC40xx board`

## Side Effects
- `[lpc17_40_adc.c:lpcxpresso_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`)
- `[lpc17_40_boot.c:lpc17_40_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `lpc17_40_sspbus_initialize()`, `lpcxpresso_sspdev_initialize()`)
- `[lpc17_40_dac.c:dac_devinit]` Initializes/registers kernel devices or filesystems (`dac_register()`)
- `[lpc17_40_leds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[lpc17_40_oled.c:board_graphics_setup]` Configures or drives hardware GPIO pins
- `[lpc17_40_oled.c:board_graphics_setup]` Initializes/registers kernel devices or filesystems (`lpc17_40_sspbus_initialize()`, `ug_initialize()`)
- `[lpc17_40_pwm.c:lpc17_40_pwminitialize]` Initializes/registers kernel devices or filesystems (`pwm_register()`)
- `[lpc17_40_ssp.c:lpcxpresso_sspdev_initialize]` Configures or drives hardware GPIO pins
- `[lpc17_40_usbmsc.c:board_usbmsc_initialize]` Initializes/registers kernel devices or filesystems (`lpc17_40_sspbus_initialize()`)

## Verification
- Run: `./tools/configure.sh lpcxpresso-lpc1768:nsh && make`
