# `verdin-mx8mp/src` Component (`boards/arm/mx8mp/verdin-mx8mp/src`)

## Overview
Board-level C implementation (`src`) for `verdin-mx8mp` (`arm/mx8mp`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 11 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[mx8mp_ina219.h:board_ina219_initialize]` Public declaration `board_ina219_initialize()`
- `[verdin-mx8mp.h:mx8mp_bringup]` Public declaration `mx8mp_bringup()`
- `[verdin-mx8mp.h:mx8mp_i2cdev_initialize]` Public declaration `mx8mp_i2cdev_initialize()`
- `[verdin-mx8mp.h:mx8mp_spidev_initialize]` Public declaration `mx8mp_spidev_initialize()`
- `[verdin-mx8mp.h:GPIO_LED_1]` Hardware/board configuration macros (`GPIO_LED_1`, `GPIO_LED_2`, `GPIO_LED_3`, `GPIO_LED_4`, `IOMUX_LED_1`, `IOMUX_LED_2` (+9 more))
- `[mx8mp_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[mx8mp_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[mx8mp_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[mx8mp_boot.c:mx8mp_board_initialize]` Public function `mx8mp_board_initialize()`
- `[mx8mp_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[mx8mp_bringup.c:rpmsg_serialinit]` Public function `rpmsg_serialinit()`
- `[mx8mp_bringup.c:mx8mp_bringup]` Public function `mx8mp_bringup()`
- `[mx8mp_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[mx8mp_buttons.c:board_buttons]` Public function `board_buttons()`
- `[mx8mp_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[mx8mp_i2cdev.c:board_i2cdev_initialize]` Public function `board_i2cdev_initialize()`
- `[mx8mp_i2cdev.c:mx8mp_i2cdev_initialize]` Public function `mx8mp_i2cdev_initialize()`
- `[mx8mp_ina219.c:board_ina219_initialize]` Public function `board_ina219_initialize()`
- `[mx8mp_spi.c:mx8mp_spi1_select]` Public function `mx8mp_spi1_select()`
- `[mx8mp_spi.c:mx8mp_spi1_status]` Public function `mx8mp_spi1_status()`
- `[mx8mp_spi.c:mx8mp_spi1_cmddata]` Public function `mx8mp_spi1_cmddata()`
- `[mx8mp_spi.c:mx8mp_spi2_select]` Public function `mx8mp_spi2_select()`
- `[mx8mp_spi.c:mx8mp_spi2_status]` Public function `mx8mp_spi2_status()`
- *(+9 additional symbols across 11 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_MX8MP_I2C_DRIVER`, `CONFIG_MX8MP_SPI_DRIVER`, `CONFIG_SENSORS_INA219`, `CONFIG_SPI`
- `[mx8mp_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[mx8mp_i2cdev.c:board_i2cdev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[mx8mp_ina219.c:board_ina219_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[mx8mp_spi.c:mx8mp_spi1_select]` Validates preconditions and returns `-ENODEV` on failure
- `[mx8mp_spidev.c:board_spidev_initialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[mx8mp_boot.c:mx8mp_board_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[mx8mp_bringup.c:rpmsg_serialinit]` Initializes/registers kernel devices or filesystems (`board_button_initialize()`, `board_ina219_initialize()`, `board_userled_initialize()`, `btn_lower_initialize()`, `mx8mp_i2cdev_initialize()`)
- `[mx8mp_buttons.c:board_button_initialize]` Modifies interrupt controller or critical-section state
- `[mx8mp_i2cdev.c:board_i2cdev_initialize]` Initializes/registers kernel devices or filesystems (`i2c_register()`, `mx8mp_i2cbus_initialize()`)
- `[mx8mp_ina219.c:board_ina219_initialize]` Initializes/registers kernel devices or filesystems (`ina219_register()`, `mx8mp_i2cbus_initialize()`)
- `[mx8mp_spidev.c:board_spidev_initialize]` Initializes/registers kernel devices or filesystems (`mx8mp_spibus_initialize()`, `spi_register()`)

## Verification
- Run: `./tools/configure.sh verdin-mx8mp:nsh && make`
