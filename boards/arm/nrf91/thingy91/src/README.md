# `thingy91/src` Component (`boards/arm/nrf91/thingy91/src`)

## Overview
Board-level C implementation (`src`) for `thingy91` (`arm/nrf91`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 9 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[thingy91.h:nrf91_bringup]` Public declaration `nrf91_bringup()`
- `[thingy91.h:nrf91_sensors_init]` Public declaration `nrf91_sensors_init()`
- `[thingy91.h:nrf91_i2c_register]` Public declaration `nrf91_i2c_register()`
- `[thingy91.h:nrf91_i2ctool]` Public declaration `nrf91_i2ctool()`
- `[thingy91.h:nrf91_spidev_initialize]` Public declaration `nrf91_spidev_initialize()`
- `[thingy91.h:nrf91_rgbled_initialize]` Public declaration `nrf91_rgbled_initialize()`
- `[thingy91.h:NRF91_PROCFS_MOUNTPOINT]` Hardware/board configuration macros (`NRF91_PROCFS_MOUNTPOINT`, `GPIO_LEDS_R`, `GPIO_LEDS_G`, `GPIO_LEDS_B`, `GPIO_LEDW_R`, `GPIO_LEDW_G` (+10 more))
- `[nrf91_boot.c:nrf91_board_initialize]` Public function `nrf91_board_initialize()`
- `[nrf91_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[nrf91_bringup.c:nrf91_bringup]` Public function `nrf91_bringup()`
- `[nrf91_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[nrf91_buttons.c:board_buttons]` Public function `board_buttons()`
- `[nrf91_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[nrf91_i2c.c:nrf91_i2c_register]` Public function `nrf91_i2c_register()`
- `[nrf91_i2c.c:nrf91_i2ctool]` Public function `nrf91_i2ctool()`
- `[nrf91_modem.c:nrf91_modem_board_init]` Public function `nrf91_modem_board_init()`
- `[nrf91_rgbled.c:nrf91_rgbled_initialize]` Public function `nrf91_rgbled_initialize()`
- `[nrf91_sensors.c:nrf91_sensors_init]` Public function `nrf91_sensors_init()`
- `[nrf91_spi.c:nrf91_spidev_initialize]` Public function `nrf91_spidev_initialize()`
- `[nrf91_spi.c:nrf91_spi0select]` Public function `nrf91_spi0select()`
- `[nrf91_spi.c:nrf91_spi0status]` Public function `nrf91_spi0status()`
- `[nrf91_spi.c:nrf91_spi1select]` Public function `nrf91_spi1select()`
- `[nrf91_spi.c:nrf91_spi1status]` Public function `nrf91_spi1status()`
- *(+4 additional symbols across 9 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_I2C`, `CONFIG_NRF91_MODEM`, `CONFIG_NRF91_SPI_MASTER`, `CONFIG_RGBLED`
- `[nrf91_rgbled.c:nrf91_rgbled_initialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[nrf91_boot.c:nrf91_board_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `nrf91_spidev_initialize()`)
- `[nrf91_bringup.c:nrf91_bringup]` Initializes/registers kernel devices or filesystems (`btn_lower_initialize()`, `nrf91_at_register()`, `nrf91_modem_initialize()`, `nrf91_rgbled_initialize()`, `nx_mount()`)
- `[nrf91_i2c.c:nrf91_i2c_register]` Initializes/registers kernel devices or filesystems (`i2c_register()`, `nrf91_i2cbus_initialize()`)
- `[nrf91_rgbled.c:nrf91_rgbled_initialize]` Initializes/registers kernel devices or filesystems (`nrf91_rgbled_register()`, `rgbled_register()`)

## Verification
- Run: `./tools/configure.sh thingy91:nsh_nrf52 && make`
