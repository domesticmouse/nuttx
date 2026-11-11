# `b-g474e-dpow1/src` Component (`boards/arm/stm32g4/b-g474e-dpow1/src`)

## Overview
Board-level C implementation (`src`) for `b-g474e-dpow1` (`arm/stm32g4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[b-g474e-dpow1.h:stm32_smps_setup]` Public declaration `stm32_smps_setup()`
- `[b-g474e-dpow1.h:GPIO_LED1]` Hardware/board configuration macros (`GPIO_LED1`, `GPIO_LED2`, `GPIO_LED3`, `GPIO_LED4`, `LED_DRIVER_PATH`)
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_smps.c:stm32_smps_setup]` Public function `stm32_smps_setup()`
- `[stm32_smps.c:g_smps_ops]` Exported global symbol `g_smps_ops`
- `[stm32_smps.c:g_smps_dev]` Exported global symbol `g_smps_dev`
- `[stm32_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[stm32_userleds.c:board_userled]` Public function `board_userled()`
- `[stm32_userleds.c:board_userled_all]` Public function `board_userled_all()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_LEDS`, `CONFIG_DRIVERS_SMPS`
- `[stm32_smps.c:#error]` Compile-time guard: `CONFIG_LIBDSP is required`
- `[stm32_smps.c:#error]` Compile-time guard: `CONFIG_ARCH_HIPRI_INTERRUPT is required`

## Side Effects
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `userled_lower_initialize()`)
- `[stm32_smps.c:stm32_smps_setup]` Configures or drives hardware GPIO pins
- `[stm32_smps.c:stm32_smps_setup]` Initializes/registers kernel devices or filesystems (`smps_register()`)
- `[stm32_smps.c:stm32_smps_setup]` Modifies interrupt controller or critical-section state
- `[stm32_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh b-g474e-dpow1:nsh && make`
