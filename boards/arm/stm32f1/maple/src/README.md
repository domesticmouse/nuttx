# `maple/src` Component (`boards/arm/stm32f1/maple/src`)

## Overview
Board-level C implementation (`src`) for `maple` (`arm/stm32f1`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 6 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[maple.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[maple.h:stm32_usbinitialize]` Public declaration `stm32_usbinitialize()`
- `[maple.h:GPIO_LED]` Hardware/board configuration macros (`GPIO_LED`, `GPIO_USB_PULLUP`, `GPIO_MEMLCD_EXTCOMIN`, `GPIO_MEMLCD_DISP`, `GPIO_MEMLCD_CS`)
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_lcd.c:board_lcd_initialize]` Public function `board_lcd_initialize()`
- `[stm32_lcd.c:board_lcd_getdev]` Public function `board_lcd_getdev()`
- `[stm32_leds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_leds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_spi.c:stm32_spidev_initialize]` Public function `stm32_spidev_initialize()`
- `[stm32_spi.c:stm32_spi1select]` Public function `stm32_spi1select()`
- `[stm32_spi.c:stm32_spi1status]` Public function `stm32_spi1status()`
- `[stm32_spi.c:stm32_spi1cmddata]` Public function `stm32_spi1cmddata()`
- `[stm32_spi.c:stm32_spi2select]` Public function `stm32_spi2select()`
- `[stm32_spi.c:stm32_spi2status]` Public function `stm32_spi2status()`
- `[stm32_usbdev.c:stm32_usbinitialize]` Public function `stm32_usbinitialize()`
- `[stm32_usbdev.c:stm32_usbpullup]` Public function `stm32_usbpullup()`
- `[stm32_usbdev.c:stm32_usbsuspend]` Public function `stm32_usbsuspend()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_BOARDCTL`, `CONFIG_INPUT`, `CONFIG_NX_LCDDRIVER`, `CONFIG_USBMSC`
- `[stm32_lcd.c:DEBUGASSERT]` Requires `freq >= 1 && freq <= 60`
- `[stm32_lcd.c:DEBUGASSERT]` Requires `spi`
- `[stm32_lcd.c:DEBUGASSERT]` Requires `tim`
- `[stm32_spi.c:stm32_spidev_initialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `stm32_spidev_initialize()`)
- `[stm32_lcd.c:board_lcd_initialize]` Configures or drives hardware GPIO pins
- `[stm32_lcd.c:board_lcd_initialize]` Initializes/registers kernel devices or filesystems (`memlcd_initialize()`, `stm32_spibus_initialize()`)
- `[stm32_leds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_spi.c:stm32_spidev_initialize]` Configures or drives hardware GPIO pins
- `[stm32_usbdev.c:stm32_usbinitialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh maple:nsh && make`
