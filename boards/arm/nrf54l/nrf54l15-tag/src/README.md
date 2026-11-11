# `nrf54l15-tag/src` Component (`boards/arm/nrf54l/nrf54l15-tag/src`)

## Overview
Board-level C implementation (`src`) for `nrf54l15-tag` (`arm/nrf54l`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 10 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[nrf54l15-tag.h:nrf54l_bringup]` Public declaration `nrf54l_bringup()`
- `[nrf54l15-tag.h:nrf54l_spidev_initialize]` Public declaration `nrf54l_spidev_initialize()`
- `[nrf54l15-tag.h:nrf54l_i2ctool]` Public declaration `nrf54l_i2ctool()`
- `[nrf54l15-tag.h:nrf54l_sensors_init]` Public declaration `nrf54l_sensors_init()`
- `[nrf54l15-tag.h:nrf54l_adc_setup]` Public declaration `nrf54l_adc_setup()`
- `[nrf54l15-tag.h:NRF54L_PROCFS_MOUNTPOINT]` Hardware/board configuration macros (`NRF54L_PROCFS_MOUNTPOINT`, `GPIO_LED1`, `GPIO_LED2`, `GPIO_LED3`, `GPIO_ANT1`, `GPIO_ANT2` (+2 more))
- `[nrf54l_adc.c:nrf54l_adc_setup]` Public function `nrf54l_adc_setup()`
- `[nrf54l_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[nrf54l_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[nrf54l_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[nrf54l_boot.c:nrf54l_board_initialize]` Public function `nrf54l_board_initialize()`
- `[nrf54l_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[nrf54l_bringup.c:nrf54l_bringup]` Public function `nrf54l_bringup()`
- `[nrf54l_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[nrf54l_buttons.c:board_buttons]` Public function `board_buttons()`
- `[nrf54l_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[nrf54l_i2c.c:nrf54l_i2c_register]` Public function `nrf54l_i2c_register()`
- `[nrf54l_i2c.c:nrf54l_i2ctool]` Public function `nrf54l_i2ctool()`
- `[nrf54l_sensors.c:nrf54l_sensors_init]` Public function `nrf54l_sensors_init()`
- `[nrf54l_spi.c:nrf54l_spidev_initialize]` Public function `nrf54l_spidev_initialize()`
- `[nrf54l_spi.c:nrf54l_spi2select]` Public function `nrf54l_spi2select()`
- `[nrf54l_spi.c:nrf54l_spi2status]` Public function `nrf54l_spi2status()`
- `[nrf54l_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- *(+2 additional symbols across 10 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_NRF54L_SAADC`, `CONFIG_NRF54L_SPI2_MASTER`, `CONFIG_SENSORS`, `CONFIG_SYSTEM_I2CTOOL`
- `[nrf54l_adc.c:nrf54l_adc_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[nrf54l_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[nrf54l_i2c.c:nrf54l_i2c_register]` Validates preconditions and returns `-ENODEV` on failure
- `[nrf54l_sensors.c:nrf54l_sensors_init]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[nrf54l_adc.c:nrf54l_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`)
- `[nrf54l_boot.c:nrf54l_board_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `nrf54l_spidev_initialize()`)
- `[nrf54l_bringup.c:nrf54l_bringup]` Initializes/registers kernel devices or filesystems (`btn_lower_initialize()`, `nrf54l_sdc_initialize()`, `nrf54l_timer_initialize()`, `nx_mount()`, `userled_lower_initialize()`)
- `[nrf54l_i2c.c:nrf54l_i2c_register]` Initializes/registers kernel devices or filesystems (`i2c_register()`, `nrf54l_i2cbus_initialize()`)
- `[nrf54l_sensors.c:nrf54l_sensors_init]` Initializes/registers kernel devices or filesystems (`adxl367_register()`, `bme688_register()`, `bmi270_register()`, `nrf54l_i2cbus_initialize()`, `nrf54l_spibus_initialize()`)

## Verification
- Run: `./tools/configure.sh nrf54l15-tag:nsh && make`
