# `nucleo-f091rc/src` Component (`boards/arm/stm32f0/nucleo-f091rc/src`)

## Overview
Board-level C implementation (`src`) for `nucleo-f091rc` (`arm/stm32f0`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[nucleo-f091rc.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[nucleo-f091rc.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[nucleo-f091rc.h:stm32_lpwaninitialize]` Public declaration `stm32_lpwaninitialize()`
- `[nucleo-f091rc.h:GPIO_LD2]` Hardware/board configuration macros (`GPIO_LD2`, `MIN_IRQBUTTON`, `MAX_IRQBUTTON`, `NUM_IRQBUTTONS`, `GPIO_BTN_USER`, `GPIO_SX127X_RESET` (+2 more))
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- `[stm32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[stm32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[stm32_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[stm32_spi.c:stm32_spidev_initialize]` Public function `stm32_spidev_initialize()`
- `[stm32_spi.c:stm32_spi1select]` Public function `stm32_spi1select()`
- `[stm32_spi.c:stm32_spi1status]` Public function `stm32_spi1status()`
- `[stm32_spi.c:stm32_spi2select]` Public function `stm32_spi2select()`
- `[stm32_spi.c:stm32_spi2status]` Public function `stm32_spi2status()`
- `[stm32_sx127x.c:stm32_lpwaninitialize]` Public function `stm32_lpwaninitialize()`
- `[stm32_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[stm32_userleds.c:board_userled]` Public function `board_userled()`
- `[stm32_userleds.c:board_userled_all]` Public function `board_userled_all()`
- `[stm32_userleds.c:stm32_led_pminitialize]` Public function `stm32_led_pminitialize()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_LPWAN_SX127X`, `CONFIG_STM32_SPI`
- `[stm32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[stm32_sx127x.c:stm32_lpwaninitialize]` Validates preconditions and returns `-EINVAL`, `-ENODEV` on failure
- `[stm32_userleds.c:DEBUGASSERT]` Requires `ret == OK`

## Side Effects
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `stm32_spidev_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`stm32_common_initialize()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_spi.c:stm32_spidev_initialize]` Configures or drives hardware GPIO pins
- `[stm32_sx127x.c:stm32_lpwaninitialize]` Configures or drives hardware GPIO pins
- `[stm32_sx127x.c:stm32_lpwaninitialize]` Initializes/registers kernel devices or filesystems (`stm32_spibus_initialize()`, `sx127x_register()`)
- `[stm32_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_userleds.c:board_userled_initialize]` Initializes/registers kernel devices or filesystems (`pm_register()`)

## Verification
- Run: `./tools/configure.sh nucleo-f091rc:nsh && make`
