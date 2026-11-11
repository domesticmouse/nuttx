# `nrf52832-dk/src` Component (`boards/arm/nrf52/nrf52832-dk/src`)

## Overview
Board-level C implementation (`src`) for `nrf52832-dk` (`arm/nrf52`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[nrf52832-dk.h:nrf52_bringup]` Public declaration `nrf52_bringup()`
- `[nrf52832-dk.h:nrf52_spidev_initialize]` Public declaration `nrf52_spidev_initialize()`
- `[nrf52832-dk.h:nrf52_mrf24j40_initialize]` Public declaration `nrf52_mrf24j40_initialize()`
- `[nrf52832-dk.h:NRF52_PROCFS_MOUNTPOINT]` Hardware/board configuration macros (`NRF52_PROCFS_MOUNTPOINT`, `GPIO_LED1`, `GPIO_LED2`, `GPIO_LED3`, `GPIO_LED4`, `GPIO_BUTTON1` (+5 more))
- `[nrf52_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[nrf52_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[nrf52_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[nrf52_boot.c:nrf52_board_initialize]` Public function `nrf52_board_initialize()`
- `[nrf52_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[nrf52_bringup.c:nrf52_bringup]` Public function `nrf52_bringup()`
- `[nrf52_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[nrf52_buttons.c:board_buttons]` Public function `board_buttons()`
- `[nrf52_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[nrf52_ieee802154_mrf24j40.c:nrf52_mrf24j40_initialize]` Public function `nrf52_mrf24j40_initialize()`
- `[nrf52_spi.c:nrf52_spidev_initialize]` Public function `nrf52_spidev_initialize()`
- `[nrf52_spi.c:nrf52_spi0select]` Public function `nrf52_spi0select()`
- `[nrf52_spi.c:nrf52_spi0status]` Public function `nrf52_spi0status()`
- `[nrf52_spi.c:nrf52_spi1select]` Public function `nrf52_spi1select()`
- `[nrf52_spi.c:nrf52_spi1status]` Public function `nrf52_spi1status()`
- `[nrf52_spi.c:nrf52_spi2select]` Public function `nrf52_spi2select()`
- `[nrf52_spi.c:nrf52_spi2status]` Public function `nrf52_spi2status()`
- `[nrf52_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[nrf52_userleds.c:board_userled]` Public function `board_userled()`
- *(+1 additional symbols across 8 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_IEEE802154_MRF24J40`, `CONFIG_NRF52_SPI_MASTER`
- `[nrf52_ieee802154_mrf24j40.c:DEBUGASSERT]` Requires `priv != NULL`
- `[nrf52_ieee802154_mrf24j40.c:DEBUGASSERT]` Requires `priv != NULL && (priv->handler != NULL || !state)`
- `[nrf52_ieee802154_mrf24j40.c:#error]` Compile-time guard: `this driver requires CONFIG_NRF52_SPI0_MASTER`

## Side Effects
- `[nrf52_boot.c:nrf52_board_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `nrf52_spidev_initialize()`)
- `[nrf52_bringup.c:nrf52_bringup]` Initializes/registers kernel devices or filesystems (`btn_lower_initialize()`, `nrf52_mrf24j40_initialize()`, `nrf52_sdc_initialize()`, `nrf52_wdt_initialize()`, `nx_mount()`)

## Verification
- Run: `./tools/configure.sh nrf52832-dk:nsh && make`
