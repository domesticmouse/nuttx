# `olimex-stm32-e407/src` Component (`boards/arm/stm32f4/olimex-stm32-e407/src`)

## Overview
Board-level C implementation (`src`) for `olimex-stm32-e407` (`arm/stm32f4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 13 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[olimex-stm32-e407.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[olimex-stm32-e407.h:stm32_usbinitialize]` Public declaration `stm32_usbinitialize()`
- `[olimex-stm32-e407.h:stm32_adc_setup]` Public declaration `stm32_adc_setup()`
- `[olimex-stm32-e407.h:stm32_sdio_initialize]` Public declaration `stm32_sdio_initialize()`
- `[olimex-stm32-e407.h:stm32_can_setup]` Public declaration `stm32_can_setup()`
- `[olimex-stm32-e407.h:stm32_dac_setup]` Public declaration `stm32_dac_setup()`
- `[olimex-stm32-e407.h:stm32_timer_driver_setup]` Public declaration `stm32_timer_driver_setup()`
- `[olimex-stm32-e407.h:stm32_mrf24j40_initialize]` Public declaration `stm32_mrf24j40_initialize()`
- `[olimex-stm32-e407.h:HAVE_USBDEV]` Hardware/board configuration macros (`HAVE_USBDEV`, `HAVE_USBHOST`, `HAVE_USBMONITOR`, `HAVE_SDIO`, `HAVE_RTC_DRIVER`, `HAVE_NETMONITOR` (+17 more))
- `[stm32_adc.c:stm32_adc_setup]` Public function `stm32_adc_setup()`
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- `[stm32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[stm32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[stm32_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[stm32_can.c:stm32_can_setup]` Public function `stm32_can_setup()`
- `[stm32_dac.c:stm32_dac_setup]` Public function `stm32_dac_setup()`
- `[stm32_mrf24j40.c:stm32_mrf24j40_initialize]` Public function `stm32_mrf24j40_initialize()`
- `[stm32_spi.c:stm32_spidev_initialize]` Public function `stm32_spidev_initialize()`
- *(+14 additional symbols across 13 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ADC`, `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_CAN`, `CONFIG_DAC` (+4 more)
- `[stm32_adc.c:stm32_adc_setup]` Validates preconditions and returns `-ENODEV`, `-ENOSYS` on failure
- `[stm32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[stm32_can.c:stm32_can_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_dac.c:stm32_dac_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_mrf24j40.c:DEBUGASSERT]` Requires `priv != NULL`
- `[stm32_mrf24j40.c:DEBUGASSERT]` Requires `priv != NULL && (priv->handler != NULL || !state)`
- `[stm32_spi.c:stm32_spidev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_usb.c:DEBUGASSERT]` Requires `iface == 0`

## Side Effects
- `[stm32_adc.c:stm32_adc_setup]` Configures or drives hardware GPIO pins
- `[stm32_adc.c:stm32_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`)
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `board_button_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`board_bmp180_initialize()`, `board_ina219_initialize()`, `i2c_register()`, `stm32_i2c_register()`, `stm32_i2cbus_initialize()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_can.c:stm32_can_setup]` Initializes/registers kernel devices or filesystems (`can_register()`)
- `[stm32_dac.c:stm32_dac_setup]` Initializes/registers kernel devices or filesystems (`dac_register()`)
- `[stm32_mrf24j40.c:stm32_mrf24j40_initialize]` Configures or drives hardware GPIO pins
- `[stm32_mrf24j40.c:stm32_mrf24j40_initialize]` Initializes/registers kernel devices or filesystems (`mac802154dev_register()`, `mac802154netdev_register()`, `stm32_spibus_initialize()`)
- `[stm32_spi.c:stm32_spidev_initialize]` Configures or drives hardware GPIO pins
- `[stm32_timer.c:stm32_timer_driver_setup]` Initializes/registers kernel devices or filesystems (`stm32_timer_initialize()`)

## Verification
- Run: `./tools/configure.sh olimex-stm32-e407:nsh && make`
