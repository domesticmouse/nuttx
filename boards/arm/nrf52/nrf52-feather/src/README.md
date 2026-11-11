# `nrf52-feather/src` Component (`boards/arm/nrf52/nrf52-feather/src`)

## Overview
Board-level C implementation (`src`) for `nrf52-feather` (`arm/nrf52`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 6 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[nrf52-feather.h:nrf52_i2c_register]` Public declaration `nrf52_i2c_register()`
- `[nrf52-feather.h:nrf52_i2ctool]` Public declaration `nrf52_i2ctool()`
- `[nrf52-feather.h:nrf52_bringup]` Public declaration `nrf52_bringup()`
- `[nrf52-feather.h:GPIO_LED1]` Hardware/board configuration macros (`GPIO_LED1`, `GPIO_LED2`)
- `[nrf52_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[nrf52_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[nrf52_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[nrf52_boot.c:nrf52_board_initialize]` Public function `nrf52_board_initialize()`
- `[nrf52_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[nrf52_bringup.c:nrf52_bringup]` Public function `nrf52_bringup()`
- `[nrf52_i2c.c:nrf52_i2c_register]` Public function `nrf52_i2c_register()`
- `[nrf52_i2c.c:nrf52_i2ctool]` Public function `nrf52_i2ctool()`
- `[nrf52_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[nrf52_userleds.c:board_userled]` Public function `board_userled()`
- `[nrf52_userleds.c:board_userled_all]` Public function `board_userled_all()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_LEDS`, `CONFIG_I2C`

## Side Effects
- `[nrf52_boot.c:nrf52_board_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[nrf52_bringup.c:nrf52_bringup]` Initializes/registers kernel devices or filesystems (`nrf52_wdt_initialize()`, `userled_lower_initialize()`)
- `[nrf52_i2c.c:nrf52_i2c_register]` Initializes/registers kernel devices or filesystems (`i2c_register()`, `nrf52_i2cbus_initialize()`)

## Verification
- Run: `./tools/configure.sh nrf52-feather:nsh && make`
