# `nucleo-l073rz/src` Component (`boards/arm/stm32l0/nucleo-l073rz/src`)

## Overview
Board-level C implementation (`src`) for `nucleo-l073rz` (`arm/stm32l0`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[nucleo-l073rz.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[nucleo-l073rz.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[nucleo-l073rz.h:stm32_wlinitialize]` Public declaration `stm32_wlinitialize()`
- `[nucleo-l073rz.h:stm32_lpwaninitialize]` Public declaration `stm32_lpwaninitialize()`
- `[nucleo-l073rz.h:GPIO_LED1]` Hardware/board configuration macros (`GPIO_LED1`, `LED_DRIVER_PATH`, `MIN_IRQBUTTON`, `MAX_IRQBUTTON`, `NUM_IRQBUTTONS`, `GPIO_BTN_USER` (+7 more))
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:stm32_usb_setpullup]` Public function `stm32_usb_setpullup()`
- `[stm32_boot.c:stm32_usb_pullup_enabled]` Public function `stm32_usb_pullup_enabled()`
- `[stm32_boot.c:stm32_usbpullup]` Public function `stm32_usbpullup()`
- `[stm32_boot.c:stm32_usbsuspend]` Public function `stm32_usbsuspend()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- `[stm32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[stm32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[stm32_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[stm32_nrf24l01.c:stm32_wlinitialize]` Public function `stm32_wlinitialize()`
- `[stm32_spi.c:stm32_spidev_initialize]` Public function `stm32_spidev_initialize()`
- `[stm32_spi.c:stm32_spi1select]` Public function `stm32_spi1select()`
- `[stm32_spi.c:stm32_spi1status]` Public function `stm32_spi1status()`
- `[stm32_spi.c:stm32_spi2select]` Public function `stm32_spi2select()`
- *(+2 additional symbols across 8 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_LPWAN_SX127X`, `CONFIG_STM32_SPI`, `CONFIG_WL_NRF24L01`
- `[stm32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[stm32_nrf24l01.c:stm32_wlinitialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_sx127x.c:stm32_lpwaninitialize]` Validates preconditions and returns `-EINVAL`, `-ENODEV` on failure

## Side Effects
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_boardinitialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `stm32_spidev_initialize()`)
- `[stm32_boot.c:stm32_boardinitialize]` Modifies interrupt controller or critical-section state
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`cdcacm_initialize()`, `stm32_common_initialize()`, `userled_lower_initialize()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_nrf24l01.c:stm32_wlinitialize]` Configures or drives hardware GPIO pins
- `[stm32_nrf24l01.c:stm32_wlinitialize]` Initializes/registers kernel devices or filesystems (`nrf24l01_register()`, `stm32_spibus_initialize()`)
- `[stm32_spi.c:stm32_spidev_initialize]` Configures or drives hardware GPIO pins
- `[stm32_sx127x.c:stm32_lpwaninitialize]` Configures or drives hardware GPIO pins
- `[stm32_sx127x.c:stm32_lpwaninitialize]` Initializes/registers kernel devices or filesystems (`stm32_spibus_initialize()`, `sx127x_register()`)

## Verification
- Run: `./tools/configure.sh nucleo-l073rz:nsh && make`
