# `olimexino-stm32/src` Component (`boards/arm/stm32f1/olimexino-stm32/src`)

## Overview
Board-level C implementation (`src`) for `olimexino-stm32` (`arm/stm32f1`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 9 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[olimexino-stm32.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[olimexino-stm32.h:stm32_usbinitialize]` Public declaration `stm32_usbinitialize()`
- `[olimexino-stm32.h:stm32_usb_set_pwr_callback]` Public declaration `stm32_usb_set_pwr_callback()`
- `[olimexino-stm32.h:stm32_led_initialize]` Public declaration `stm32_led_initialize()`
- `[olimexino-stm32.h:board_usbmsc_initialize]` Public declaration `board_usbmsc_initialize()`
- `[olimexino-stm32.h:stm32_can_setup]` Public declaration `stm32_can_setup()`
- `[olimexino-stm32.h:GPIO_LED1]` Hardware/board configuration macros (`GPIO_LED1`, `GPIO_LED_GREEN`, `GPIO_LED2`, `GPIO_LED_YELLOW`, `BUTTON_BOOT0N`, `IRQBUTTON` (+4 more))
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[stm32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[stm32_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[stm32_can.c:stm32_can_setup]` Public function `stm32_can_setup()`
- `[stm32_composite.c:board_composite_initialize]` Public function `board_composite_initialize()`
- `[stm32_composite.c:board_composite_connect]` Public function `board_composite_connect()`
- `[stm32_leds.c:board_userled]` Public function `board_userled()`
- `[stm32_leds.c:board_userled_all]` Public function `board_userled_all()`
- `[stm32_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_leds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_spi.c:stm32_spidev_initialize]` Public function `stm32_spidev_initialize()`
- `[stm32_spi.c:stm32_spi1select]` Public function `stm32_spi1select()`
- `[stm32_spi.c:stm32_spi1status]` Public function `stm32_spi1status()`
- `[stm32_spi.c:stm32_spi2select]` Public function `stm32_spi2select()`
- *(+11 additional symbols across 9 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_STM32_CAN_CHARDRIVER`, `CONFIG_USBDEV`, `CONFIG_USBDEV_COMPOSITE`, `CONFIG_USBMSC`
- `[stm32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[stm32_can.c:stm32_can_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_composite.c:DEBUGASSERT]` Requires `g_mschandle == NULL`
- `[stm32_composite.c:DEBUGASSERT]` Requires `g_mschandle != NULL`
- `[stm32_composite.c:#error]` Compile-time guard: `Unrecognized STM32 board`
- `[stm32_spi.c:stm32_spidev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_usbmsc.c:#error]` Compile-time guard: `Unrecognized STM32 board`

## Side Effects
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_button_initialize()`, `board_composite_initialize()`, `board_usbmsc_initialize()`, `stm32_led_initialize()`, `stm32_spidev_initialize()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_can.c:stm32_can_setup]` Initializes/registers kernel devices or filesystems (`can_register()`)
- `[stm32_composite.c:board_composite_initialize]` Initializes/registers kernel devices or filesystems (`composite_initialize()`, `stm32_spibus_initialize()`)
- `[stm32_leds.c:board_userled]` Configures or drives hardware GPIO pins
- `[stm32_leds.c:board_userled]` Initializes/registers kernel devices or filesystems (`board_userled_initialize()`, `led_initialize()`, `stm32_led_initialize()`)
- `[stm32_spi.c:stm32_spidev_initialize]` Configures or drives hardware GPIO pins
- `[stm32_usbdev.c:stm32_usb_set_pwr_callback]` Configures or drives hardware GPIO pins
- `[stm32_usbmsc.c:board_usbmsc_initialize]` Initializes/registers kernel devices or filesystems (`stm32_spibus_initialize()`)

## Verification
- Run: `./tools/configure.sh olimexino-stm32:nsh && make`
