# `nrf54lm20-dk/src` Component (`boards/arm/nrf54l/nrf54lm20-dk/src`)

## Overview
Board-level C implementation (`src`) for `nrf54lm20-dk` (`arm/nrf54l`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 6 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[nrf54lm20-dk.h:nrf54l_bringup]` Public declaration `nrf54l_bringup()`
- `[nrf54lm20-dk.h:nrf54l_ieee802154_initialize]` Public declaration `nrf54l_ieee802154_initialize()`
- `[nrf54lm20-dk.h:NRF54L_PROCFS_MOUNTPOINT]` Hardware/board configuration macros (`NRF54L_PROCFS_MOUNTPOINT`, `GPIO_LED1`, `GPIO_LED2`, `GPIO_LED3`, `GPIO_LED4`)
- `[nrf54l_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[nrf54l_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[nrf54l_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[nrf54l_boot.c:nrf54l_board_initialize]` Public function `nrf54l_board_initialize()`
- `[nrf54l_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[nrf54l_bringup.c:nrf54l_bringup]` Public function `nrf54l_bringup()`
- `[nrf54l_ieee802154.c:nrf54l_ieee802154_initialize]` Public function `nrf54l_ieee802154_initialize()`
- `[nrf54l_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[nrf54l_userleds.c:board_userled]` Public function `board_userled()`
- `[nrf54l_userleds.c:board_userled_all]` Public function `board_userled_all()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_LEDS`, `CONFIG_NRF54L_RADIO_IEEE802154`
- `[nrf54l_ieee802154.c:nrf54l_ieee802154_initialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[nrf54l_boot.c:nrf54l_board_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[nrf54l_bringup.c:nrf54l_bringup]` Initializes/registers kernel devices or filesystems (`nrf54l_ieee802154_initialize()`, `nrf54l_sdc_initialize()`, `nx_mount()`, `userled_lower_initialize()`)
- `[nrf54l_ieee802154.c:nrf54l_ieee802154_initialize]` Initializes/registers kernel devices or filesystems (`mac802154dev_register()`, `mac802154netdev_register()`, `nrf54l_radioi8_register()`)

## Verification
- Run: `./tools/configure.sh nrf54lm20-dk:nsh && make`
