# `beagleplay/src` Component (`boards/arm64/am62x/beagleplay/src`)

## Overview
Board-level C implementation (`src`) for `beagleplay` (`arm64/am62x`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[beagleplay.h:beagleplay_bringup]` Public declaration `beagleplay_bringup()`
- `[beagleplay.h:beagleplay_led_initialize]` Public declaration `beagleplay_led_initialize()`
- `[beagleplay_autoleds.c:beagleplay_led_initialize]` Public function `beagleplay_led_initialize()`
- `[beagleplay_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[beagleplay_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[beagleplay_boardinit.c:am62x_memory_initialize]` Public function `am62x_memory_initialize()`
- `[beagleplay_boardinit.c:am62x_board_initialize]` Public function `am62x_board_initialize()`
- `[beagleplay_boardinit.c:board_late_initialize]` Public function `board_late_initialize()`
- `[beagleplay_bringup.c:beagleplay_bringup]` Public function `beagleplay_bringup()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_LEDS`
- `[beagleplay_bringup.c:beagleplay_bringup]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[beagleplay_boardinit.c:am62x_memory_initialize]` Initializes/registers kernel devices or filesystems (`beagleplay_led_initialize()`)
- `[beagleplay_bringup.c:beagleplay_bringup]` Initializes/registers kernel devices or filesystems (`am62x_gpio_initialize()`, `am62x_i2cbus_initialize()`, `am62x_i2cdev_register()`, `am62x_tisci_initialize()`, `i2c_register()`)

## Verification
- Run: `./tools/configure.sh beagleplay:nsh && make`
