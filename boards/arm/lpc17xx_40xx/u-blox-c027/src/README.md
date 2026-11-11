# `u-blox-c027/src` Component (`boards/arm/lpc17xx_40xx/u-blox-c027/src`)

## Overview
Board-level C implementation (`src`) for `u-blox-c027` (`arm/lpc17xx_40xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 9 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[u-blox-c027.h:c027_sspdev_initialize]` Public declaration `c027_sspdev_initialize()`
- `[u-blox-c027.h:lpc17_40_ubxmdm_init]` Public declaration `lpc17_40_ubxmdm_init()`
- `[u-blox-c027.h:lpc17_40_pwm_setup]` Public declaration `lpc17_40_pwm_setup()`
- `[u-blox-c027.h:lpc17_40_adc_setup]` Public declaration `lpc17_40_adc_setup()`
- `[u-blox-c027.h:C027_LED]` Hardware/board configuration macros (`C027_LED`, `C027_SD_CS`, `C027_SD_CD`, `GPSADDR`, `GPSBAUD`, `MDMBAUD` (+9 more))
- `[lpc17_40_adc.c:lpc17_40_adc_setup]` Public function `lpc17_40_adc_setup()`
- `[lpc17_40_boot.c:lpc17_40_boardinitialize]` Public function `lpc17_40_boardinitialize()`
- `[lpc17_40_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[lpc17_40_dac.c:dac_devinit]` Public function `dac_devinit()`
- `[lpc17_40_leds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[lpc17_40_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[lpc17_40_leds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[lpc17_40_pwm.c:lpc17_40_pwminitialize]` Public function `lpc17_40_pwminitialize()`
- `[lpc17_40_pwm.c:lpc17_40_mcpwminitialize]` Public function `lpc17_40_mcpwminitialize()`
- `[lpc17_40_pwm.c:lpc17_40_timerinitialize]` Public function `lpc17_40_timerinitialize()`
- `[lpc17_40_pwm.c:lpc17_40_pwm_setup]` Public function `lpc17_40_pwm_setup()`
- `[lpc17_40_ssp.c:c027_sspdev_initialize]` Public function `c027_sspdev_initialize()`
- `[lpc17_40_ssp.c:lpc17_40_ssp0select]` Public function `lpc17_40_ssp0select()`
- `[lpc17_40_ssp.c:lpc17_40_ssp0status]` Public function `lpc17_40_ssp0status()`
- `[lpc17_40_ssp.c:lpc17_40_ssp1select]` Public function `lpc17_40_ssp1select()`
- `[lpc17_40_ssp.c:lpc17_40_ssp1status]` Public function `lpc17_40_ssp1status()`
- `[lpc17_40_ubxmdm.c:lpc17_40_ubxmdm_init]` Public function `lpc17_40_ubxmdm_init()`
- `[lpc17_40_usbmsc.c:board_usbmsc_initialize]` Public function `board_usbmsc_initialize()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ADC`, `CONFIG_MODEM_U_BLOX`, `CONFIG_PWM`, `CONFIG_USBMSC`
- `[lpc17_40_adc.c:lpc17_40_adc_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[lpc17_40_boot.c:#error]` Compile-time guard: `Unrecognized board`
- `[lpc17_40_dac.c:dac_devinit]` Validates preconditions and returns `-ENODEV` on failure
- `[lpc17_40_pwm.c:lpc17_40_pwminitialize]` Validates preconditions and returns `-ENODEV` on failure
- `[lpc17_40_ubxmdm.c:DEBUGASSERT]` Requires `status->register_values_size >= UBXMDM_REGISTER_COUNT`
- `[lpc17_40_ubxmdm.c:DEBUGASSERT]` Requires `priv->ops == NULL && priv->pins == NULL`
- `[lpc17_40_usbmsc.c:#error]` Compile-time guard: `Unrecognized LPC17xx/LPC40xx board`

## Side Effects
- `[lpc17_40_adc.c:lpc17_40_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`)
- `[lpc17_40_boot.c:lpc17_40_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `c027_sspdev_initialize()`, `lpc17_40_sspbus_initialize()`, `nx_mount()`)
- `[lpc17_40_dac.c:dac_devinit]` Initializes/registers kernel devices or filesystems (`dac_register()`)
- `[lpc17_40_leds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[lpc17_40_pwm.c:lpc17_40_pwminitialize]` Initializes/registers kernel devices or filesystems (`pwm_register()`)
- `[lpc17_40_ssp.c:c027_sspdev_initialize]` Configures or drives hardware GPIO pins
- `[lpc17_40_ubxmdm.c:lpc17_40_ubxmdm_init]` Configures or drives hardware GPIO pins
- `[lpc17_40_ubxmdm.c:lpc17_40_ubxmdm_init]` Initializes/registers kernel devices or filesystems (`ubxmdm_register()`)
- `[lpc17_40_usbmsc.c:board_usbmsc_initialize]` Initializes/registers kernel devices or filesystems (`lpc17_40_sspbus_initialize()`)

## Verification
- Run: `./tools/configure.sh u-blox-c027:nsh && make`
