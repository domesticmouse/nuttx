# `rm57l843-launchxl2/src` Component (`boards/arm/rm57/rm57l843-launchxl2/src`)

## Overview
Board-level C implementation (`src`) for `rm57l843-launchxl2` (`arm/rm57`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 11 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[rm57l843-launchxl2.h:rm57_bringup]` Public declaration `rm57_bringup()`
- `[rm57l843-launchxl2.h:rm57_can_setup]` Public declaration `rm57_can_setup()`
- `[rm57l843-launchxl2.h:rm57_adc_setup]` Public declaration `rm57_adc_setup()`
- `[rm57l843-launchxl2.h:rm57_spi_setup]` Public declaration `rm57_spi_setup()`
- `[rm57l843-launchxl2.h:rm57_i2c_setup]` Public declaration `rm57_i2c_setup()`
- `[rm57l843-launchxl2.h:rm57_eth_setup]` Public declaration `rm57_eth_setup()`
- `[rm57l843-launchxl2.h:rm57_phy_powerup]` Public declaration `rm57_phy_powerup()`
- `[rm57l843-launchxl2.h:GIO_LED_B6]` Hardware/board configuration macros (`GIO_LED_B6`, `GIO_LED_B7`, `GIO_BUTTON_B4`, `GIO_BUTTON_B5`, `GIO_PHY_PWRDOWN`, `GIO_PHY_RESET`)
- `[rm57_adc.c:rm57_adc_setup]` Public function `rm57_adc_setup()`
- `[rm57_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[rm57_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[rm57_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[rm57_bringup.c:rm57_bringup]` Public function `rm57_bringup()`
- `[rm57_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[rm57_buttons.c:board_buttons]` Public function `board_buttons()`
- `[rm57_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[rm57_can.c:rm57_can_setup]` Public function `rm57_can_setup()`
- `[rm57_ethernet.c:rm57_phy_powerup]` Public function `rm57_phy_powerup()`
- `[rm57_ethernet.c:rm57_eth_setup]` Public function `rm57_eth_setup()`
- `[rm57_i2c.c:rm57_i2c_setup]` Public function `rm57_i2c_setup()`
- `[rm57_initialize.c:rm57_board_initialize]` Public function `rm57_board_initialize()`
- `[rm57_initialize.c:board_late_initialize]` Public function `board_late_initialize()`
- `[rm57_spi.c:rm57_mibspi1select]` Public function `rm57_mibspi1select()`
- *(+18 additional symbols across 11 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_NETDEV_LATEINIT`, `CONFIG_RM57_ADC`, `CONFIG_RM57_DCAN`, `CONFIG_RM57_EMAC` (+2 more)
- `[rm57_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[rm57_i2c.c:rm57_i2c_setup]` Validates preconditions and returns `-EIO`, `-ENODEV` on failure
- `[rm57_spi.c:rm57_mibspi1select]` Validates preconditions and returns `-EIO`, `-ENODEV` on failure

## Side Effects
- `[rm57_adc.c:rm57_adc_setup]` Initializes/registers kernel devices or filesystems (`rm57_adc_initialize()`, `rm57_adc_temp_register()`)
- `[rm57_bringup.c:rm57_bringup]` Initializes/registers kernel devices or filesystems (`board_button_initialize()`, `board_userled_initialize()`, `nx_mount()`)
- `[rm57_buttons.c:board_button_initialize]` Modifies interrupt controller or critical-section state
- `[rm57_can.c:rm57_can_setup]` Initializes/registers kernel devices or filesystems (`rm57_dcan_chardev_initialize()`, `rm57_dcan_sock_initialize()`)
- `[rm57_i2c.c:rm57_i2c_setup]` Initializes/registers kernel devices or filesystems (`i2c_register()`, `rm57_i2cbus_initialize()`)
- `[rm57_initialize.c:rm57_board_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[rm57_spi.c:rm57_mibspi1select]` Initializes/registers kernel devices or filesystems (`rm57_mibspibus_initialize()`, `spi_register()`)

## Verification
- Run: `./tools/configure.sh rm57l843-launchxl2:nsh && make`
