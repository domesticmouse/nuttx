# `beaglebone/src` Component (`boards/arm/am335x/beaglebone/src`)

## Overview
Board-level C implementation (`src`) for `beaglebone` (`arm/am335x`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[beaglebone.h:am335x_bringup]` Public declaration `am335x_bringup()`
- `[beaglebone.h:am335x_led_initialize]` Public declaration `am335x_led_initialize()`
- `[beaglebone.h:GPIO_LED0]` Hardware/board configuration macros (`GPIO_LED0`, `GPIO_LED1`, `GPIO_LED2`, `GPIO_LED3`)
- `[am335x_boot.c:am335x_memory_initialize]` Public function `am335x_memory_initialize()`
- `[am335x_boot.c:am335x_board_initialize]` Public function `am335x_board_initialize()`
- `[am335x_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[am335x_bringup.c:am335x_bringup]` Public function `am335x_bringup()`
- `[am335x_leds.c:am335x_led_initialize]` Public function `am335x_led_initialize()`
- `[am335x_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[am335x_leds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[am335x_leds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[am335x_leds.c:board_userled]` Public function `board_userled()`
- `[am335x_leds.c:board_userled_all]` Public function `board_userled_all()`

## Invariants
- None

## Side Effects
- `[am335x_boot.c:am335x_memory_initialize]` Initializes/registers kernel devices or filesystems (`am335x_led_initialize()`)
- `[am335x_bringup.c:am335x_bringup]` Initializes/registers kernel devices or filesystems (`am335x_can_initialize()`, `am335x_can_register()`, `am335x_i2c_register()`, `am335x_i2cbus_initialize()`, `can_register()`)

## Verification
- Run: `./tools/configure.sh beaglebone:nsh && make`
