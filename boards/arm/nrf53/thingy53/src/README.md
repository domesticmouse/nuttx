# `thingy53/src` Component (`boards/arm/nrf53/thingy53/src`)

## Overview
Board-level C implementation (`src`) for `thingy53` (`arm/nrf53`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 13 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[thingy53.h:nrf53_bringup]` Public declaration `nrf53_bringup()`
- `[thingy53.h:nrf53_sensors_init]` Public declaration `nrf53_sensors_init()`
- `[thingy53.h:nrf53_rgbled_initialize]` Public declaration `nrf53_rgbled_initialize()`
- `[thingy53.h:nrf53_i2c_register]` Public declaration `nrf53_i2c_register()`
- `[thingy53.h:nrf53_i2ctool]` Public declaration `nrf53_i2ctool()`
- `[thingy53.h:nrf53_spidev_initialize]` Public declaration `nrf53_spidev_initialize()`
- `[thingy53.h:nrf53_adc_setup]` Public declaration `nrf53_adc_setup()`
- `[thingy53.h:nrf53_npm1100_init]` Public declaration `nrf53_npm1100_init()`
- `[thingy53.h:NRF53_PROCFS_MOUNTPOINT]` Hardware/board configuration macros (`NRF53_PROCFS_MOUNTPOINT`, `GPIO_LED_R`, `GPIO_LED_G`, `GPIO_LED_B`, `GPIO_BUTTON1`, `GPIO_BUTTON2` (+19 more))
- `[nrf53_adc.c:nrf53_adc_setup]` Public function `nrf53_adc_setup()`
- `[nrf53_boot.c:nrf53_board_initialize]` Public function `nrf53_board_initialize()`
- `[nrf53_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[nrf53_bringup.c:rpmsg_serialinit]` Public function `rpmsg_serialinit()`
- `[nrf53_bringup.c:nrf53_bringup]` Public function `nrf53_bringup()`
- `[nrf53_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[nrf53_buttons.c:board_buttons]` Public function `board_buttons()`
- `[nrf53_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[nrf53_composite.c:board_composite0_connect]` Public function `board_composite0_connect()`
- `[nrf53_composite.c:board_composite_initialize]` Public function `board_composite_initialize()`
- `[nrf53_composite.c:board_composite_connect]` Public function `board_composite_connect()`
- `[nrf53_cpunet_boot.c:nrf53_board_gpio_cpunet_allow]` Public function `nrf53_board_gpio_cpunet_allow()`
- `[nrf53_i2c.c:nrf53_i2c_register]` Public function `nrf53_i2c_register()`
- `[nrf53_i2c.c:nrf53_i2ctool]` Public function `nrf53_i2ctool()`
- *(+15 additional symbols across 13 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ADC`, `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_I2C`, `CONFIG_NPM1100`, `CONFIG_NRF53_APPCORE` (+4 more)
- `[nrf53_adc.c:nrf53_adc_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[nrf53_bringup.c:#error]` Compile-time guard: `# endif`
- `[nrf53_composite.c:DEBUGASSERT]` Requires `epin <= NRF53_NENDPOINTS`
- `[nrf53_composite.c:DEBUGASSERT]` Requires `epout <= NRF53_NENDPOINTS`
- `[nrf53_npm1100.c:nrf53_npm1100_init]` Validates preconditions and returns `-ENODEV` on failure
- `[nrf53_rgbled.c:#error]` Compile-time guard: `Invalid configuration for RGBLED driver`

## Side Effects
- `[nrf53_adc.c:nrf53_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`)
- `[nrf53_boot.c:nrf53_board_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `nrf53_spidev_initialize()`)
- `[nrf53_bringup.c:rpmsg_serialinit]` Initializes/registers kernel devices or filesystems (`bt_driver_register()`, `btn_lower_initialize()`, `nrf53_rgbled_initialize()`, `nrf53_rpmsghci_server_initialize()`, `nrf53_sdc_initialize()`)
- `[nrf53_composite.c:board_composite0_connect]` Initializes/registers kernel devices or filesystems (`composite_initialize()`)
- `[nrf53_i2c.c:nrf53_i2c_register]` Initializes/registers kernel devices or filesystems (`i2c_register()`, `nrf53_i2cbus_initialize()`)
- `[nrf53_npm1100.c:nrf53_npm1100_init]` Initializes/registers kernel devices or filesystems (`battery_charger_register()`, `npm1100_initialize()`)
- `[nrf53_rgbled.c:nrf53_rgbled_initialize]` Initializes/registers kernel devices or filesystems (`rgbled_register()`)
- `[nrf53_sensors.c:nrf53_sensors_init]` Initializes/registers kernel devices or filesystems (`nrf53_bmi270spi_initialize()`)

## Verification
- Run: `./tools/configure.sh thingy53:composite_cpuapp && make`
