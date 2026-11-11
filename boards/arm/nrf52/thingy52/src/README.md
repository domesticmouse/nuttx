# `thingy52/src` Component (`boards/arm/nrf52/thingy52/src`)

## Overview
Board-level C implementation (`src`) for `thingy52` (`arm/nrf52`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[thingy52.h:nrf52_bringup]` Public declaration `nrf52_bringup()`
- `[thingy52.h:nrf52_sensors_init]` Public declaration `nrf52_sensors_init()`
- `[thingy52.h:nrf52_adc_setup]` Public declaration `nrf52_adc_setup()`
- `[thingy52.h:nrf52_sx1509_initialize]` Public declaration `nrf52_sx1509_initialize()`
- `[thingy52.h:nrf52_ccs811_wake]` Public declaration `nrf52_ccs811_wake()`
- `[thingy52.h:nrf52_sx1509_get]` Public declaration `nrf52_sx1509_get()`
- `[thingy52.h:nrf52_rgbled_initialize]` Public declaration `nrf52_rgbled_initialize()`
- `[thingy52.h:NRF52_PROCFS_MOUNTPOINT]` Hardware/board configuration macros (`NRF52_PROCFS_MOUNTPOINT`, `GPIO_BUTTON1`, `LIS2DH12_I2C_ADDR`, `GPIO_LIS2DH12_INT`, `MPU9250_I2C_ADDR`, `GPIO_MPU9250_INT` (+10 more))
- `[nrf52_adc.c:nrf52_adc_setup]` Public function `nrf52_adc_setup()`
- `[nrf52_boot.c:nrf52_board_initialize]` Public function `nrf52_board_initialize()`
- `[nrf52_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[nrf52_bringup.c:nrf52_bringup]` Public function `nrf52_bringup()`
- `[nrf52_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[nrf52_buttons.c:board_buttons]` Public function `board_buttons()`
- `[nrf52_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[nrf52_rgbled.c:nrf52_rgbled_initialize]` Public function `nrf52_rgbled_initialize()`
- `[nrf52_sensors.c:nrf52_sensors_init]` Public function `nrf52_sensors_init()`
- `[nrf52_sx1509.c:nrf52_ccs811_wake]` Public function `nrf52_ccs811_wake()`
- `[nrf52_sx1509.c:nrf52_sx1509_get]` Public function `nrf52_sx1509_get()`
- `[nrf52_sx1509.c:nrf52_sx1509_initialize]` Public function `nrf52_sx1509_initialize()`
- `[nrf52_sx1509.c:g_sx1509_cfg]` Exported global symbol `g_sx1509_cfg`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ADC`, `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_IOEXPANDER_PWM`, `CONFIG_IOEXPANDER_SX1509`, `CONFIG_NRF52_I2C0_MASTER` (+1 more)
- `[nrf52_adc.c:nrf52_adc_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[nrf52_rgbled.c:nrf52_rgbled_initialize]` Validates preconditions and returns `-ENODEV`, `-ENOTTY` on failure
- `[nrf52_sensors.c:nrf52_sensors_init]` Validates preconditions and returns `-ENODEV` on failure
- `[nrf52_sx1509.c:#error]` Compile-time guard: `INT pin not supported`

## Side Effects
- `[nrf52_adc.c:nrf52_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`)
- `[nrf52_boot.c:nrf52_board_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[nrf52_bringup.c:nrf52_bringup]` Initializes/registers kernel devices or filesystems (`btn_lower_initialize()`, `i2c_register()`, `nrf52_i2c_register()`, `nrf52_i2cbus_initialize()`, `nrf52_rgbled_initialize()`)
- `[nrf52_rgbled.c:nrf52_rgbled_initialize]` Initializes/registers kernel devices or filesystems (`rgbled_register()`)
- `[nrf52_sensors.c:nrf52_sensors_init]` Initializes/registers kernel devices or filesystems (`nrf52_i2cbus_initialize()`)
- `[nrf52_sx1509.c:nrf52_ccs811_wake]` Initializes/registers kernel devices or filesystems (`nrf52_i2cbus_initialize()`, `sx1509_initialize()`, `sx1509_leds_initialize()`)

## Verification
- Run: `./tools/configure.sh thingy52:nsh && make`
