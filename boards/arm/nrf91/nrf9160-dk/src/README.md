# `nrf9160-dk/src` Component (`boards/arm/nrf91/nrf9160-dk/src`)

## Overview
Board-level C implementation (`src`) for `nrf9160-dk` (`arm/nrf91`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[nrf9160-dk.h:nrf91_bringup]` Public declaration `nrf91_bringup()`
- `[nrf9160-dk.h:NRF91_PROCFS_MOUNTPOINT]` Hardware/board configuration macros (`NRF91_PROCFS_MOUNTPOINT`, `GPIO_LED1`, `GPIO_LED2`, `GPIO_LED3`, `GPIO_LED4`, `GPIO_BUTTON1` (+1 more))
- `[nrf91_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[nrf91_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[nrf91_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[nrf91_boot.c:nrf91_board_initialize]` Public function `nrf91_board_initialize()`
- `[nrf91_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[nrf91_bringup.c:arm_netinitialize]` Public function `arm_netinitialize()`
- `[nrf91_bringup.c:nrf91_bringup]` Public function `nrf91_bringup()`
- `[nrf91_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[nrf91_buttons.c:board_buttons]` Public function `board_buttons()`
- `[nrf91_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[nrf91_modem.c:nrf91_modem_board_init]` Public function `nrf91_modem_board_init()`
- `[nrf91_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[nrf91_userleds.c:board_userled]` Public function `board_userled()`
- `[nrf91_userleds.c:board_userled_all]` Public function `board_userled_all()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_NRF91_MODEM`

## Side Effects
- `[nrf91_boot.c:nrf91_board_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[nrf91_bringup.c:arm_netinitialize]` Initializes/registers kernel devices or filesystems (`btn_lower_initialize()`, `nrf91_at_register()`, `nrf91_gnss_register()`, `nrf91_modem_initialize()`, `nx_mount()`)

## Verification
- Run: `./tools/configure.sh nrf9160-dk:nsh && make`
