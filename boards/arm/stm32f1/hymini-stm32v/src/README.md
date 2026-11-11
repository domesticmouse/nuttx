# `hymini-stm32v/src` Component (`boards/arm/stm32f1/hymini-stm32v/src`)

## Overview
Board-level C implementation (`src`) for `hymini-stm32v` (`arm/stm32f1`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 10 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[hymini-stm32v.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[hymini-stm32v.h:stm32_usbinitialize]` Public declaration `stm32_usbinitialize()`
- `[hymini-stm32v.h:stm32_tsc_setup]` Public declaration `stm32_tsc_setup()`
- `[hymini-stm32v.h:GPIO_LED1]` Hardware/board configuration macros (`GPIO_LED1`, `GPIO_LED2`, `MIN_IRQBUTTON`, `MAX_IRQBUTTON`, `NUM_IRQBUTTONS`, `GPIO_BTN_KEYA` (+5 more))
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[stm32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[stm32_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[stm32_leds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_leds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_r61505u.c:write_cmd]` Public function `write_cmd()`
- `[stm32_r61505u.c:read_data]` Public function `read_data()`
- `[stm32_r61505u.c:write_data]` Public function `write_data()`
- `[stm32_r61505u.c:board_lcd_initialize]` Public function `board_lcd_initialize()`
- `[stm32_r61505u.c:board_lcd_getdev]` Public function `board_lcd_getdev()`
- `[stm32_r61505u.c:board_lcd_uninitialize]` Public function `board_lcd_uninitialize()`
- `[stm32_r61505u.c:lcd_clear]` Public function `lcd_clear()`
- `[stm32_spi.c:stm32_spidev_initialize]` Public function `stm32_spidev_initialize()`
- `[stm32_spi.c:stm32_spi1select]` Public function `stm32_spi1select()`
- `[stm32_spi.c:stm32_spi1status]` Public function `stm32_spi1status()`
- `[stm32_spi.c:stm32_spi2select]` Public function `stm32_spi2select()`
- *(+11 additional symbols across 10 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_INPUT`, `CONFIG_LCD_R61505U`, `CONFIG_LCD_SSD1289`, `CONFIG_USBMSC`
- `[stm32_boot.c:#error]` Compile-time guard: `Only one MMC/SD slot`
- `[stm32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[stm32_r61505u.c:DEBUGASSERT]` Requires `buffer && ((uintptr_t)buffer & 1) == 0`
- `[stm32_r61505u.c:DEBUGASSERT]` Requires `dev && vinfo`
- `[stm32_r61505u.c:#error]` Compile-time guard: `CONFIG_STM32_FSMC is required for LCD support`
- `[stm32_r61505u.c:#error]` Compile-time guard: `RGB color mapping not supported by this driver`
- `[stm32_ssd1289.c:DEBUGASSERT]` Requires `power <= CONFIG_LCD_MAXPOWER`
- `[stm32_ssd1289.c:DEBUGASSERT]` Requires `lcddev == 0`
- `[stm32_ssd1289.c:#error]` Compile-time guard: `CONFIG_STM32_FSMC is required to use the LCD`
- `[stm32_ts.c:#error]` Compile-time guard: `CONFIG_STM32_SPI1 must be defined to use the ADS7843 on this board`
- `[stm32_usbmsc.c:#error]` Compile-time guard: `Unrecognized STM32 board`

## Side Effects
- `[stm32_boot.c:stm32_boardinitialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `sdio_initialize()`, `stm32_spidev_initialize()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_leds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_r61505u.c:write_cmd]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[stm32_r61505u.c:write_cmd]` Configures or drives hardware GPIO pins
- `[stm32_r61505u.c:write_cmd]` Initializes/registers kernel devices or filesystems (`lcd_initialize()`)
- `[stm32_spi.c:stm32_spidev_initialize]` Configures or drives hardware GPIO pins
- `[stm32_ssd1289.c:board_lcd_initialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[stm32_ssd1289.c:board_lcd_initialize]` Configures or drives hardware GPIO pins
- `[stm32_ts.c:stm32_tsc_setup]` Configures or drives hardware GPIO pins
- `[stm32_ts.c:stm32_tsc_setup]` Initializes/registers kernel devices or filesystems (`ads7843e_register()`, `stm32_spibus_initialize()`)

## Verification
- Run: `./tools/configure.sh hymini-stm32v:nsh && make`
