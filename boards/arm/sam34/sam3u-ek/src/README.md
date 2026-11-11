# `sam3u-ek/src` Component (`boards/arm/sam34/sam3u-ek/src`)

## Overview
Board-level C implementation (`src`) for `sam3u-ek` (`arm/sam34`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 10 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[sam3u-ek.h:sam_spidev_initialize]` Public declaration `sam_spidev_initialize()`
- `[sam3u-ek.h:sam_hsmciinit]` Public declaration `sam_hsmciinit()`
- `[sam3u-ek.h:sam_cardinserted]` Public declaration `sam_cardinserted()`
- `[sam3u-ek.h:sam_writeprotected]` Public declaration `sam_writeprotected()`
- `[sam3u-ek.h:sam_tsc_setup]` Public declaration `sam_tsc_setup()`
- `[sam3u-ek.h:LCD_BASE]` Hardware/board configuration macros (`LCD_BASE`, `CONFIG_TSC_ADS7843`, `CONFIG_TSC_SPI`, `GPIO_LCD_NCS2`, `GPIO_LCD_RS`, `GPIO_LCD_NWE` (+31 more))
- `[sam_boot.c:sam_boardinitialize]` Public function `sam_boardinitialize()`
- `[sam_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[sam_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[sam_buttons.c:board_buttons]` Public function `board_buttons()`
- `[sam_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[sam_lcd.c:board_lcd_initialize]` Public function `board_lcd_initialize()`
- `[sam_lcd.c:board_lcd_getdev]` Public function `board_lcd_getdev()`
- `[sam_lcd.c:board_lcd_uninitialize]` Public function `board_lcd_uninitialize()`
- `[sam_leds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[sam_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[sam_leds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[sam_mmcsd.c:sam_hsmciinit]` Public function `sam_hsmciinit()`
- `[sam_mmcsd.c:sam_cardinserted]` Public function `sam_cardinserted()`
- `[sam_mmcsd.c:sam_writeprotected]` Public function `sam_writeprotected()`
- `[sam_spi.c:sam_spidev_initialize]` Public function `sam_spidev_initialize()`
- `[sam_spi.c:sam_spi0select]` Public function `sam_spi0select()`
- `[sam_spi.c:sam_spi0status]` Public function `sam_spi0status()`
- *(+3 additional symbols across 10 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_INPUT_ADS7843E`, `CONFIG_LCD`, `CONFIG_SAM34_HSMCI`, `CONFIG_USBMSC`
- `[sam_boot.c:#error]` Compile-time guard: `Only one MMC/SD slot`
- `[sam_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[sam_lcd.c:DEBUGASSERT]` Requires `buffer && ((uintptr_t)buffer & 1) == 0`
- `[sam_lcd.c:DEBUGASSERT]` Requires `dev && vinfo`
- `[sam_lcd.c:#error]` Compile-time guard: `CONFIG_LCD_MAXCONTRAST must be defined in the range 1 to 31`
- `[sam_lcd.c:#error]` Compile-time guard: `RGB color mapping not supported by this driver`
- `[sam_touchscreen.c:DEBUGASSERT]` Requires `minor == 0`
- `[sam_touchscreen.c:#error]` Compile-time guard: `Touchscreen support requires CONFIG_INPUT`
- `[sam_touchscreen.c:#error]` Compile-time guard: `Touchscreen support requires CONFIG_SAM34_SPI0`
- `[sam_usbmsc.c:board_usbmsc_initialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[sam_boot.c:sam_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `sam_spidev_initialize()`, `sdio_initialize()`)
- `[sam_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[sam_buttons.c:board_button_initialize]` Modifies interrupt controller or critical-section state
- `[sam_lcd.c:board_lcd_initialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[sam_lcd.c:board_lcd_initialize]` Configures or drives hardware GPIO pins
- `[sam_leds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[sam_mmcsd.c:sam_hsmciinit]` Configures or drives hardware GPIO pins
- `[sam_spi.c:sam_spidev_initialize]` Configures or drives hardware GPIO pins
- `[sam_touchscreen.c:sam_tsc_setup]` Configures or drives hardware GPIO pins
- `[sam_touchscreen.c:sam_tsc_setup]` Initializes/registers kernel devices or filesystems (`ads7843e_register()`, `sam_spibus_initialize()`)
- `[sam_touchscreen.c:sam_tsc_setup]` Modifies interrupt controller or critical-section state
- `[sam_usbmsc.c:board_usbmsc_initialize]` Initializes/registers kernel devices or filesystems (`sdio_initialize()`)

## Verification
- Run: `./tools/configure.sh sam3u-ek:nsh && make`
