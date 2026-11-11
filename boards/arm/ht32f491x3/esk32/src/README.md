# `esk32/src` Component (`boards/arm/ht32f491x3/esk32/src`)

## Overview
Board-level C implementation (`src`) for `esk32` (`arm/ht32f491x3`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[ht32_boot.c:ht32f491x3_clockconfig]` Public function `ht32f491x3_clockconfig()`
- `[ht32_boot.c:ht32f491x3_boardinitialize]` Public function `ht32f491x3_boardinitialize()`
- `[ht32_bringup.c:board_late_initialize]` Public function `board_late_initialize()`
- `[ht32_pwm.c:ht32_pwm_setup]` Public function `ht32_pwm_setup()`
- `[ht32_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[ht32_userleds.c:board_userled]` Public function `board_userled()`
- `[ht32_userleds.c:board_userled_all]` Public function `board_userled_all()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_BOARD_LATE_INITIALIZE`, `CONFIG_PWM`, `CONFIG_USERLED`
- `[ht32_bringup.c:board_late_initialize]` Validates preconditions and returns `-EBUSY`, `-EEXIST` on failure
- `[ht32_pwm.c:ht32_pwm_setup]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[ht32_boot.c:ht32f491x3_clockconfig]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[ht32_bringup.c:board_late_initialize]` Initializes/registers kernel devices or filesystems (`board_userled_initialize()`, `nx_mount()`, `userled_lower_initialize()`)
- `[ht32_pwm.c:ht32_pwm_setup]` Initializes/registers kernel devices or filesystems (`pwm_register()`)
- `[ht32_userleds.c:board_userled_initialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[ht32_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh esk32:nsh && make`
