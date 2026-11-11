# `quickfeather/src` Component (`boards/arm/eoss3/quickfeather/src`)

## Overview
Board-level C implementation (`src`) for `quickfeather` (`arm/eoss3`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[quickfeather.h:eoss3_bringup]` Public declaration `eoss3_bringup()`
- `[quickfeather.h:EOSS3_PROCFS_MOUNTPOINT]` Hardware/board configuration macros (`EOSS3_PROCFS_MOUNTPOINT`)
- `[eoss3_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[eoss3_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[eoss3_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[eoss3_boot.c:eoss3_boardinitialize]` Public function `eoss3_boardinitialize()`
- `[eoss3_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[eoss3_bringup.c:eoss3_bringup]` Public function `eoss3_bringup()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_LEDS`

## Side Effects
- `[eoss3_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[eoss3_boot.c:eoss3_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)

## Verification
- Run: `./tools/configure.sh quickfeather:nsh && make`
