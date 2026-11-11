# `nrf52840-dk/src` Component (`boards/arm/nrf52/nrf52840-dk/src`)

## Overview
Board-level C implementation (`src`) for `nrf52840-dk` (`arm/nrf52`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 19 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[nrf52840-dk.h:nrf52_bringup]` Public declaration `nrf52_bringup()`
- `[nrf52840-dk.h:nrf52_spidev_initialize]` Public declaration `nrf52_spidev_initialize()`
- `[nrf52840-dk.h:nrf52_lsm6dsl_initialize]` Public declaration `nrf52_lsm6dsl_initialize()`
- `[nrf52840-dk.h:nrf52_lsm303agr_initialize]` Public declaration `nrf52_lsm303agr_initialize()`
- `[nrf52840-dk.h:nrf52_hts221_initialize]` Public declaration `nrf52_hts221_initialize()`
- `[nrf52840-dk.h:nrf52_lpwaninitialize]` Public declaration `nrf52_lpwaninitialize()`
- `[nrf52840-dk.h:nrf52_pwm_setup]` Public declaration `nrf52_pwm_setup()`
- `[nrf52840-dk.h:nrf52_adc_setup]` Public declaration `nrf52_adc_setup()`
- `[nrf52840-dk.h:nrf52_mx25_initialize]` Public declaration `nrf52_mx25_initialize()`
- `[nrf52840-dk.h:nrf52_gpioleds_initialize]` Public declaration `nrf52_gpioleds_initialize()`
- `[nrf52840-dk.h:nrf52_qencoder_initialize]` Public declaration `nrf52_qencoder_initialize()`
- `[nrf52840-dk.h:NRF52_PROCFS_MOUNTPOINT]` Hardware/board configuration macros (`NRF52_PROCFS_MOUNTPOINT`, `GPIO_LED1`, `GPIO_LED2`, `GPIO_LED3`, `GPIO_LED4`, `GPIO_BUTTON1` (+6 more))
- `[nrf52_adc.c:nrf52_adc_setup]` Public function `nrf52_adc_setup()`
- `[nrf52_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[nrf52_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[nrf52_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[nrf52_boot.c:nrf52_board_initialize]` Public function `nrf52_board_initialize()`
- `[nrf52_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[nrf52_bringup.c:nrf52_bringup]` Public function `nrf52_bringup()`
- `[nrf52_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[nrf52_buttons.c:board_buttons]` Public function `board_buttons()`
- `[nrf52_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[nrf52_composite.c:board_composite0_connect]` Public function `board_composite0_connect()`
- *(+25 additional symbols across 19 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ADC`, `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_LPWAN_SX127X`, `CONFIG_NRF52840DK_BTNLEDS_GPIO` (+10 more)
- `[nrf52_adc.c:nrf52_adc_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[nrf52_composite.c:DEBUGASSERT]` Requires `epin <= NRF52_NENDPOINTS`
- `[nrf52_composite.c:DEBUGASSERT]` Requires `epout <= NRF52_NENDPOINTS`
- `[nrf52_highpri.c:#error]` Compile-time guard: `CONFIG_ARCH_HIPRI_INTERRUPT is required`
- `[nrf52_highpri.c:#error]` Compile-time guard: `CONFIG_ARCH_RAMVECTORS is required`
- `[nrf52_hts221.c:#error]` Compile-time guard: `HTS221 driver requires CONFIG_NRF52_I2C0_MASTER to be enabled`
- `[nrf52_lsm303agr.c:#error]` Compile-time guard: `LSM303AGR driver requires CONFIG_NRF52_I2C0_MASTER to be enabled`
- `[nrf52_lsm6dsl.c:#error]` Compile-time guard: `LSM6DSL driver requires CONFIG_NRF52_I2C0_MASTER to be enabled`
- `[nrf52_pwm.c:nrf52_pwm_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[nrf52_qencoder.c:nrf52_qencoder_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[nrf52_sx127x.c:nrf52_lpwaninitialize]` Validates preconditions and returns `-EINVAL`, `-ENODEV` on failure

## Side Effects
- `[nrf52_adc.c:nrf52_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`)
- `[nrf52_boot.c:nrf52_board_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `nrf52_spidev_initialize()`)
- `[nrf52_bringup.c:nrf52_bringup]` Initializes/registers kernel devices or filesystems (`btn_lower_initialize()`, `i2c_register()`, `nrf52_gpioleds_initialize()`, `nrf52_hts221_initialize()`, `nrf52_i2c_register()`)
- `[nrf52_composite.c:board_composite0_connect]` Initializes/registers kernel devices or filesystems (`composite_initialize()`)
- `[nrf52_gpio.c:nrf52_gpioleds_initialize]` Initializes/registers kernel devices or filesystems (`gpio_pin_register()`)
- `[nrf52_highpri.c:timer_handler]` Modifies interrupt controller or critical-section state
- `[nrf52_hts221.c:nrf52_hts221_initialize]` Initializes/registers kernel devices or filesystems (`nrf52_i2cbus_initialize()`)
- `[nrf52_hts221.c:nrf52_hts221_initialize]` Modifies interrupt controller or critical-section state
- `[nrf52_lsm303agr.c:nrf52_lsm303agr_initialize]` Initializes/registers kernel devices or filesystems (`lsm303agr_sensor_register()`, `nrf52_i2cbus_initialize()`)
- `[nrf52_lsm6dsl.c:nrf52_lsm6dsl_initialize]` Initializes/registers kernel devices or filesystems (`lsm6dsl_sensor_register()`, `nrf52_i2cbus_initialize()`)
- `[nrf52_mx25.c:nrf52_mx25_initialize]` Initializes/registers kernel devices or filesystems (`mx25rxx_initialize()`, `nrf52_qspi_initialize()`, `nx_mount()`)
- `[nrf52_pwm.c:nrf52_pwm_setup]` Initializes/registers kernel devices or filesystems (`pwm_register()`)

## Verification
- Run: `./tools/configure.sh nrf52840-dk:nsh && make`
