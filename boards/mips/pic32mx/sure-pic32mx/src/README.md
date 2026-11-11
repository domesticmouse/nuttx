# `sure-pic32mx/src` Component (`boards/mips/pic32mx/sure-pic32mx/src`)

## Overview
Board-level C implementation (`src`) for `sure-pic32mx` (`mips/pic32mx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[sure-pic32mx.h:pic32mx_spidev_initialize]` Public declaration `pic32mx_spidev_initialize()`
- `[sure-pic32mx.h:pic32mx_usbdevinitialize]` Public declaration `pic32mx_usbdevinitialize()`
- `[sure-pic32mx.h:pic32mx_led_initialize]` Public declaration `pic32mx_led_initialize()`
- `[sure-pic32mx.h:GPIO_USB_LED]` Hardware/board configuration macros (`GPIO_USB_LED`, `GPIO_SD_LED`, `GPIO_FLASH_LED`, `GPIO_ERROR_LED`, `GPIO_LCD_RS`, `GPIO_LCD_RW` (+4 more))
- `[pic32mx_autoleds.c:pic32mx_led_initialize]` Public function `pic32mx_led_initialize()`
- `[pic32mx_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[pic32mx_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[pic32mx_boot.c:pic32mx_boardinitialize]` Public function `pic32mx_boardinitialize()`
- `[pic32mx_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[pic32mx_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[pic32mx_buttons.c:board_buttons]` Public function `board_buttons()`
- `[pic32mx_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[pic32mx_lcd1602.c:up_lcd1602_initialize]` Public function `up_lcd1602_initialize()`
- `[pic32mx_spi.c:pic32mx_spidev_initialize]` Public function `pic32mx_spidev_initialize()`
- `[pic32mx_spi.c:pic32mx_spi2select]` Public function `pic32mx_spi2select()`
- `[pic32mx_spi.c:pic32mx_spi2status]` Public function `pic32mx_spi2status()`
- `[pic32mx_usbdev.c:pic32mx_usbdevinitialize]` Public function `pic32mx_usbdevinitialize()`
- `[pic32mx_usbdev.c:pic32mx_usbpullup]` Public function `pic32mx_usbpullup()`
- `[pic32mx_usbdev.c:pic32mx_usbsuspend]` Public function `pic32mx_usbsuspend()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_DBDP11215`, `CONFIG_ARCH_LEDS`, `CONFIG_LCD_LCD1602`, `CONFIG_PIC32MX_USBDEV`
- `[pic32mx_boot.c:pic32mx_boardinitialize]` Validates preconditions and returns `-ENODEV`, `-ENOEXEC` on failure
- `[pic32mx_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[pic32mx_lcd1602.c:up_lcd1602_initialize]` Validates preconditions and returns `-EINVAL`, `-ENOTTY`, `-ERANGE` on failure

## Side Effects
- `[pic32mx_autoleds.c:pic32mx_led_initialize]` Configures or drives hardware GPIO pins
- `[pic32mx_boot.c:pic32mx_boardinitialize]` Initializes/registers kernel devices or filesystems (`pic32_usbhost_initialize()`, `pic32mx_led_initialize()`, `pic32mx_spibus_initialize()`, `pic32mx_spidev_initialize()`, `up_lcd1602_initialize()`)
- `[pic32mx_buttons.c:board_button_initialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[pic32mx_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[pic32mx_lcd1602.c:up_lcd1602_initialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[pic32mx_lcd1602.c:up_lcd1602_initialize]` Configures or drives hardware GPIO pins
- `[pic32mx_lcd1602.c:up_lcd1602_initialize]` Initializes/registers kernel devices or filesystems (`register_driver()`)
- `[pic32mx_spi.c:pic32mx_spidev_initialize]` Configures or drives hardware GPIO pins
- `[pic32mx_usbdev.c:pic32mx_usbdevinitialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh sure-pic32mx:nsh && make`
