# `arduino-nano-33ble/src` Component (`boards/arm/nrf52/arduino-nano-33ble/src`)

## Overview
Board-level C implementation (`src`) for `arduino-nano-33ble` (`arm/nrf52`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[arduino-nano-33ble.h:nrf52_bringup]` Public declaration `nrf52_bringup()`
- `[arduino-nano-33ble.h:nrf52_lsm9ds1_initialize]` Public declaration `nrf52_lsm9ds1_initialize()`
- `[arduino-nano-33ble.h:GPIO_LED1]` Hardware/board configuration macros (`GPIO_LED1`, `GPIO_LED2`, `GPIO_LED3`, `GPIO_LED4`, `GPIO_LED5`)
- `[nrf52_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[nrf52_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[nrf52_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[nrf52_boot.c:nrf52_board_initialize]` Public function `nrf52_board_initialize()`
- `[nrf52_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[nrf52_bringup.c:nrf52_bringup]` Public function `nrf52_bringup()`
- `[nrf52_composite.c:board_composite0_connect]` Public function `board_composite0_connect()`
- `[nrf52_composite.c:board_composite_initialize]` Public function `board_composite_initialize()`
- `[nrf52_composite.c:board_composite_connect]` Public function `board_composite_connect()`
- `[nrf52_lsm9ds1.c:nrf52_lsm9ds1_initialize]` Public function `nrf52_lsm9ds1_initialize()`
- `[nrf52_usb.c:nrf52_usbsuspend]` Public function `nrf52_usbsuspend()`
- `[nrf52_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[nrf52_userleds.c:board_userled]` Public function `board_userled()`
- `[nrf52_userleds.c:board_userled_all]` Public function `board_userled_all()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_LEDS`, `CONFIG_SENSORS_LSM9DS1`, `CONFIG_USBDEV`, `CONFIG_USBDEV_COMPOSITE`
- `[nrf52_composite.c:DEBUGASSERT]` Requires `epin <= NRF52_NENDPOINTS`
- `[nrf52_composite.c:DEBUGASSERT]` Requires `epout <= NRF52_NENDPOINTS`
- `[nrf52_lsm9ds1.c:#error]` Compile-time guard: `LSM9DS1 driver requires CONFIG_NRF52_I2C0_MASTER to be enabled`

## Side Effects
- `[nrf52_boot.c:nrf52_board_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[nrf52_bringup.c:nrf52_bringup]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[nrf52_bringup.c:nrf52_bringup]` Initializes/registers kernel devices or filesystems (`i2c_register()`, `nrf52_i2c_register()`, `nrf52_i2cbus_initialize()`, `nrf52_lsm9ds1_initialize()`, `userled_lower_initialize()`)
- `[nrf52_composite.c:board_composite0_connect]` Initializes/registers kernel devices or filesystems (`composite_initialize()`)
- `[nrf52_lsm9ds1.c:nrf52_lsm9ds1_initialize]` Initializes/registers kernel devices or filesystems (`lsm9ds1accel_register()`, `lsm9ds1gyro_register()`, `lsm9ds1mag_register()`, `nrf52_i2cbus_initialize()`)

## Verification
- Run: `./tools/configure.sh arduino-nano-33ble:nsh && make`
