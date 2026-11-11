# `pic32mx7mmb/src` Component (`boards/mips/pic32mx/pic32mx7mmb/src`)

## Overview
Board-level C implementation (`src`) for `pic32mx7mmb` (`mips/pic32mx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 9 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[pic32mx7mmb.h:pic32mx_spidev_initialize]` Public declaration `pic32mx_spidev_initialize()`
- `[pic32mx7mmb.h:pic32mx_led_initialize]` Public declaration `pic32mx_led_initialize()`
- `[pic32mx7mmb.h:pic32mx_bringup]` Public declaration `pic32mx_bringup()`
- `[pic32mx7mmb.h:pic32mx_lcdinitialize]` Public declaration `pic32mx_lcdinitialize()`
- `[pic32mx7mmb.h:pic32mx_tsc_setup]` Public declaration `pic32mx_tsc_setup()`
- `[pic32_boot.c:pic32mx_boardinitialize]` Public function `pic32mx_boardinitialize()`
- `[pic32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[pic32_bringup.c:pic32mx_bringup]` Public function `pic32mx_bringup()`
- `[pic32_leds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[pic32_leds.c:board_userled]` Public function `board_userled()`
- `[pic32_leds.c:board_userled_all]` Public function `board_userled_all()`
- `[pic32_leds.c:pic32mx_led_initialize]` Public function `pic32mx_led_initialize()`
- `[pic32_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[pic32_leds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[pic32_mio283qt2.c:board_lcd_initialize]` Public function `board_lcd_initialize()`
- `[pic32_mio283qt2.c:board_lcd_getdev]` Public function `board_lcd_getdev()`
- `[pic32_mio283qt2.c:board_lcd_uninitialize]` Public function `board_lcd_uninitialize()`
- `[pic32_mio283qt2.c:pic32mx_lcdinitialize]` Public function `pic32mx_lcdinitialize()`
- `[pic32_spi.c:pic32mx_spidev_initialize]` Public function `pic32mx_spidev_initialize()`
- `[pic32_spi.c:pic32mx_spi1select]` Public function `pic32mx_spi1select()`
- `[pic32_spi.c:pic32mx_spi1status]` Public function `pic32mx_spi1status()`
- `[pic32_spi.c:pic32mx_spi1cmddata]` Public function `pic32mx_spi1cmddata()`
- `[pic32_spi.c:pic31mx_spi2select]` Public function `pic31mx_spi2select()`
- `[pic32_spi.c:pic31mx_spi2status]` Public function `pic31mx_spi2status()`
- *(+12 additional symbols across 9 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_INPUT`, `CONFIG_PIC32MX_USBDEV`, `CONFIG_USBMSC`
- `[pic32_bringup.c:#error]` Compile-time guard: `CONFIG_PIC32MX_USBHOST is not selected`
- `[pic32_mio283qt2.c:DEBUGASSERT]` Requires `lcddev == 0`
- `[pic32_mio283qt2.c:#error]` Compile-time guard: `CONFIG_PIC32MX_PMP is required to use the LCD`
- `[pic32_touchscreen.c:DEBUGASSERT]` Requires `priv != NULL`
- `[pic32_touchscreen.c:DEBUGASSERT]` Requires `ret == 0`
- `[pic32_touchscreen.c:DEBUGASSERT]` Requires `inode->i_private`

## Side Effects
- `[pic32_boot.c:pic32mx_boardinitialize]` Initializes/registers kernel devices or filesystems (`pic32mx_led_initialize()`, `pic32mx_spidev_initialize()`)
- `[pic32_bringup.c:pic32mx_bringup]` Initializes/registers kernel devices or filesystems (`nx_mount()`, `pic32_usbhost_initialize()`, `pic32mx_spibus_initialize()`, `usbhost_cdcacm_initialize()`, `usbhost_msc_initialize()`)
- `[pic32_leds.c:board_userled_initialize]` Configures or drives hardware GPIO pins
- `[pic32_mio283qt2.c:board_lcd_initialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[pic32_mio283qt2.c:board_lcd_initialize]` Configures or drives hardware GPIO pins
- `[pic32_spi.c:pic32mx_spidev_initialize]` Configures or drives hardware GPIO pins
- `[pic32_touchscreen.c:pic32mx_tsc_setup]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[pic32_touchscreen.c:pic32mx_tsc_setup]` Initializes/registers kernel devices or filesystems (`register_driver()`)
- `[pic32_touchscreen.c:pic32mx_tsc_setup]` Modifies interrupt controller or critical-section state
- `[pic32_usbdev.c:pic32mx_usbdevinitialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh pic32mx7mmb:nsh && make`
