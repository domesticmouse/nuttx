# `lpc4337-ws/src` Component (`boards/arm/lpc43xx/lpc4337-ws/src`)

## Overview
Board-level C implementation (`src`) for `lpc4337-ws` (`arm/lpc43xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 3 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[lpc4337-ws.h:lpc43_adc_setup]` Public declaration `lpc43_adc_setup()`
- `[lpc4337-ws.h:HAVE_I2CTOOL]` Hardware/board configuration macros (`HAVE_I2CTOOL`)
- `[lpc43_adc.c:lpc43_adc_setup]` Public function `lpc43_adc_setup()`
- `[lpc43_boot.c:lpc43_boardinitialize]` Public function `lpc43_boardinitialize()`
- `[lpc43_boot.c:board_late_initialize]` Public function `board_late_initialize()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_LPC43_ADC0`
- `[lpc43_adc.c:lpc43_adc_setup]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[lpc4337-ws.h:lpc43_adc_setup]` Configures or drives hardware GPIO pins
- `[lpc43_adc.c:lpc43_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`)
- `[lpc43_boot.c:lpc43_boardinitialize]` Initializes/registers kernel devices or filesystems (`i2c_register()`, `lpc43_i2c_register()`, `lpc43_i2cbus_initialize()`)

## Verification
- Run: `./tools/configure.sh lpc4337-ws:nsh && make`
