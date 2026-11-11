# `lpc4370-link2/src` Component (`boards/arm/lpc43xx/lpc4370-link2/src`)

## Overview
Board-level C implementation (`src`) for `lpc4370-link2` (`arm/lpc43xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 6 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[lpc4370-link2.h:board_spifi_initialize]` Public declaration `board_spifi_initialize()`
- `[lpc4370-link2.h:lpc43_adc_setup]` Public declaration `lpc43_adc_setup()`
- `[lpc4370-link2.h:HAVE_I2CTOOL]` Hardware/board configuration macros (`HAVE_I2CTOOL`, `PINCONFIG_LED`, `GPIO_LED`)
- `[lpc43_adc.c:lpc43_adc_setup]` Public function `lpc43_adc_setup()`
- `[lpc43_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[lpc43_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[lpc43_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[lpc43_boot.c:lpc43_boardinitialize]` Public function `lpc43_boardinitialize()`
- `[lpc43_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[lpc43_spifilib_init.c:board_spifi_initialize]` Public function `board_spifi_initialize()`
- `[lpc43_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[lpc43_userleds.c:board_userled]` Public function `board_userled()`
- `[lpc43_userleds.c:board_userled_all]` Public function `board_userled_all()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_LEDS`, `CONFIG_LPC43_ADC0`, `CONFIG_SPIFI_LIBRARY`, `CONFIG_USBMSC`
- `[lpc43_adc.c:lpc43_adc_setup]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[lpc4370-link2.h:board_spifi_initialize]` Configures or drives hardware GPIO pins
- `[lpc43_adc.c:lpc43_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`)
- `[lpc43_boot.c:lpc43_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `board_spifi_initialize()`, `i2c_register()`, `lpc43_i2c_register()`, `lpc43_i2cbus_initialize()`)
- `[lpc43_spifilib_init.c:board_spifi_initialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[lpc43_spifilib_init.c:board_spifi_initialize]` Modifies interrupt controller or critical-section state

## Verification
- Run: `./tools/configure.sh lpc4370-link2:nsh && make`
