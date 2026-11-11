# `b-l475e-iot01a/src` Component (`boards/arm/stm32l4/b-l475e-iot01a/src`)

## Overview
Board-level C implementation (`src`) for `b-l475e-iot01a` (`arm/stm32l4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[b-l475e-iot01a.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[b-l475e-iot01a.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[b-l475e-iot01a.h:stm32_timer_driver_setup]` Public declaration `stm32_timer_driver_setup()`
- `[b-l475e-iot01a.h:stm32_spirit_initialize]` Public declaration `stm32_spirit_initialize()`
- `[b-l475e-iot01a.h:HAVE_SPSGRF]` Hardware/board configuration macros (`HAVE_SPSGRF`, `HAVE_MX25R6435F`, `HAVE_MX25R6435F_SMARTFS`, `GPIO_LED1`, `GPIO_LED2`, `GPIO_SPSGRF_CS` (+2 more))
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_boot.c:stm32_board_initialize]` Public function `stm32_board_initialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- `[stm32_spi.c:stm32_spidev_initialize]` Public function `stm32_spidev_initialize()`
- `[stm32_spi.c:stm32_spi1select]` Public function `stm32_spi1select()`
- `[stm32_spi.c:stm32_spi1status]` Public function `stm32_spi1status()`
- `[stm32_spi.c:stm32_spi2select]` Public function `stm32_spi2select()`
- `[stm32_spi.c:stm32_spi2status]` Public function `stm32_spi2status()`
- `[stm32_spi.c:stm32_spi3select]` Public function `stm32_spi3select()`
- `[stm32_spi.c:stm32_spi3status]` Public function `stm32_spi3status()`
- `[stm32_spi.c:stm32_spi1cmddata]` Public function `stm32_spi1cmddata()`
- `[stm32_spi.c:stm32_spi2cmddata]` Public function `stm32_spi2cmddata()`
- `[stm32_spi.c:stm32_spi3cmddata]` Public function `stm32_spi3cmddata()`
- `[stm32_spirit.c:stm32_spirit_initialize]` Public function `stm32_spirit_initialize()`
- `[stm32_timer.c:stm32_timer_driver_setup]` Public function `stm32_timer_driver_setup()`
- *(+3 additional symbols across 8 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_LEDS`, `CONFIG_SPIRIT_NETDEV`
- `[stm32_bringup.c:stm32_bringup]` Validates preconditions and returns `-EIO` on failure
- `[stm32_spirit.c:DEBUGASSERT]` Requires `priv != NULL`
- `[stm32_spirit.c:DEBUGASSERT]` Requires `priv != NULL && (priv->handler != NULL || !state)`
- `[stm32_spirit.c:#error]` Compile-time guard: `Wireless support requires CONFIG_DRIVERS_WIRELESS`

## Side Effects
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_board_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `stm32_spidev_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`board_userled_initialize()`, `mx25rxx_initialize()`, `nx_mount()`, `smart_initialize()`, `stm32_qspi_initialize()`)
- `[stm32_spi.c:stm32_spidev_initialize]` Configures or drives hardware GPIO pins
- `[stm32_spi.c:stm32_spidev_initialize]` Initializes/registers kernel devices or filesystems (`stm32_spibus_initialize()`)
- `[stm32_spirit.c:stm32_spirit_initialize]` Configures or drives hardware GPIO pins
- `[stm32_spirit.c:stm32_spirit_initialize]` Initializes/registers kernel devices or filesystems (`spirit_netdev_initialize()`, `stm32_spibus_initialize()`)
- `[stm32_timer.c:stm32_timer_driver_setup]` Initializes/registers kernel devices or filesystems (`stm32_timer_initialize()`)
- `[stm32_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh b-l475e-iot01a:nsh && make`
