# `arduino-r4-minima/src` Component (`boards/arm/ra4/arduino-r4-minima/src`)

## Overview
Board-level C implementation (`src`) for `arduino-r4-minima` (`arm/ra4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 6 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[arduino-r4-minima.h:ra4m1_bringup]` Public declaration `ra4m1_bringup()`
- `[ra4m1_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[ra4m1_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[ra4m1_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[ra4m1_boot.c:ra_boardinitialize]` Public function `ra_boardinitialize()`
- `[ra4m1_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[ra4m1_bringup.c:ra4m1_pwm_setup]` Public function `ra4m1_pwm_setup()`
- `[ra4m1_bringup.c:ra4m1_bringup]` Public function `ra4m1_bringup()`
- `[ra4m1_pwm.c:ra4m1_pwm_setup]` Public function `ra4m1_pwm_setup()`
- `[ra4m1_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[ra4m1_userleds.c:board_userled]` Public function `board_userled()`
- `[ra4m1_userleds.c:board_userled_all]` Public function `board_userled_all()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_LEDS`, `CONFIG_PWM`
- `[ra4m1_pwm.c:ra4m1_pwm_setup]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[ra4m1_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[ra4m1_boot.c:ra_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[ra4m1_bringup.c:ra4m1_pwm_setup]` Initializes/registers kernel devices or filesystems (`board_userled_initialize()`, `userled_lower_initialize()`)
- `[ra4m1_pwm.c:ra4m1_pwm_setup]` Initializes/registers kernel devices or filesystems (`pwm_register()`)
- `[ra4m1_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh arduino-r4-minima:nsh && make`
