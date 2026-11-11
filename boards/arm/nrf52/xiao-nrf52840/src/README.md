# `xiao-nrf52840/src` Component (`boards/arm/nrf52/xiao-nrf52840/src`)

## Overview
Board-level C implementation (`src`) for `xiao-nrf52840` (`arm/nrf52`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[xiao-nrf52840.h:nrf52_gpio_initialize]` Public declaration `nrf52_gpio_initialize()`
- `[xiao-nrf52840.h:nrf52_bringup]` Public declaration `nrf52_bringup()`
- `[xiao-nrf52840.h:NRF52_PROCFS_MOUNTPOINT]` Hardware/board configuration macros (`NRF52_PROCFS_MOUNTPOINT`, `GPIO_LED1`, `GPIO_LED2`, `GPIO_LED3`, `BOARD_NGPIOIN`, `BOARD_NGPIOOUT` (+4 more))
- `[nrf52_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[nrf52_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[nrf52_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[nrf52_boot.c:nrf52_board_initialize]` Public function `nrf52_board_initialize()`
- `[nrf52_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[nrf52_bringup.c:nrf52_bringup]` Public function `nrf52_bringup()`
- `[nrf52_composite.c:board_composite0_connect]` Public function `board_composite0_connect()`
- `[nrf52_composite.c:board_composite_initialize]` Public function `board_composite_initialize()`
- `[nrf52_composite.c:board_composite_connect]` Public function `board_composite_connect()`
- `[nrf52_gpio.c:nrf52_gpio_initialize]` Public function `nrf52_gpio_initialize()`
- `[nrf52_usb.c:nrf52_usbsuspend]` Public function `nrf52_usbsuspend()`
- `[nrf52_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[nrf52_userleds.c:board_userled]` Public function `board_userled()`
- `[nrf52_userleds.c:board_userled_all]` Public function `board_userled_all()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_LEDS`, `CONFIG_DEV_GPIO`, `CONFIG_USBDEV`, `CONFIG_USBDEV_COMPOSITE`
- `[nrf52_composite.c:DEBUGASSERT]` Requires `epin <= NRF52_NENDPOINTS`
- `[nrf52_composite.c:DEBUGASSERT]` Requires `epout <= NRF52_NENDPOINTS`
- `[nrf52_gpio.c:DEBUGASSERT]` Requires `nrf52gpint != NULL && nrf52gpint->callback != NULL`
- `[nrf52_gpio.c:DEBUGASSERT]` Requires `nrf52gpio != NULL && value != NULL`
- `[nrf52_gpio.c:DEBUGASSERT]` Requires `nrf52gpio->id < BOARD_NGPIOIN`

## Side Effects
- `[nrf52_boot.c:nrf52_board_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[nrf52_bringup.c:nrf52_bringup]` Initializes/registers kernel devices or filesystems (`nrf52_gpio_initialize()`, `nrf52_ieee802154_initialize()`, `nx_mount()`, `userled_lower_initialize()`)
- `[nrf52_composite.c:board_composite0_connect]` Initializes/registers kernel devices or filesystems (`composite_initialize()`)
- `[nrf52_gpio.c:nrf52_gpio_initialize]` Initializes/registers kernel devices or filesystems (`gpio_pin_register()`)

## Verification
- Run: `./tools/configure.sh xiao-nrf52840:nsh && make`
