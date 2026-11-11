# `hpm6360evk/src` Component (`boards/risc-v/hpm6000/hpm6360evk/src`)

## Overview
Board-level C implementation (`src`) for `hpm6360evk` (`risc-v/hpm6000`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[hpm6360evk.h:hpm6360_bringup]` Public declaration `hpm6360_bringup()`
- `[hpm6360evk.h:hpm6360_autoled_initialize]` Public declaration `hpm6360_autoled_initialize()`
- `[hpm6360evk.h:GPIO_LED]` Hardware/board configuration macros (`GPIO_LED`, `LED_DRIVER_PATH`)
- `[hpm6360_autoleds.c:hpm6360_autoled_initialize]` Public function `hpm6360_autoled_initialize()`
- `[hpm6360_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[hpm6360_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[hpm6360_boot.c:hpm6360_boardinitialize]` Public function `hpm6360_boardinitialize()`
- `[hpm6360_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[hpm6360_bringup.c:hpm6360_bringup]` Public function `hpm6360_bringup()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_LEDS`

## Side Effects
- `[hpm6360_boot.c:hpm6360_boardinitialize]` Initializes/registers kernel devices or filesystems (`hpm6360_autoled_initialize()`)
- `[hpm6360_bringup.c:hpm6360_bringup]` Initializes/registers kernel devices or filesystems (`nx_mount()`)

## Verification
- Run: `./tools/configure.sh hpm6360evk:nsh && make`
