# `nvmpg-stm32f1/src` Component (`boards/arm/stm32f1/nvmpg-stm32f1/src`)

## Overview
Board-level C implementation (`src`) for `nvmpg-stm32f1` (`arm/stm32f1`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[nvmpg-stm32f1.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[nvmpg-stm32f1.h:stm32_gpio_initialize]` Public declaration `stm32_gpio_initialize()`
- `[nvmpg-stm32f1.h:GPIO_LCD_DATA]` Hardware/board configuration macros (`GPIO_LCD_DATA`, `GPIO_LCD_WR`, `GPIO_LCD_RS`, `GPIO_LCD_CS`, `GPIO_LCD_RD`, `GPIO_KEY` (+10 more))
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- `[stm32_gpio.c:stm32_gpio_initialize]` Public function `stm32_gpio_initialize()`
- `[stm32_ili9225.c:board_lcd_initialize]` Public function `board_lcd_initialize()`
- `[stm32_ili9225.c:board_lcd_getdev]` Public function `board_lcd_getdev()`
- `[stm32_ili9225.c:board_lcd_uninitialize]` Public function `board_lcd_uninitialize()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_DEV_GPIO`, `CONFIG_LCD`
- `[stm32_gpio.c:DEBUGASSERT]` Requires `stm32gpio != NULL && value != NULL`
- `[stm32_gpio.c:DEBUGASSERT]` Requires `stm32gpio->id < NVMPG_NKEYS`
- `[stm32_ili9225.c:DEBUGASSERT]` Requires `buffer != NULL && ((uintptr_t)buffer & 1) == 0`
- `[stm32_ili9225.c:DEBUGASSERT]` Requires `row < LCD_YRES && col + npixels <= LCD_XRES`

## Side Effects
- `[stm32_boot.c:stm32_boardinitialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`board_lcd_initialize()`, `lcddev_register()`, `stm32_gpio_initialize()`)
- `[stm32_gpio.c:stm32_gpio_initialize]` Configures or drives hardware GPIO pins
- `[stm32_gpio.c:stm32_gpio_initialize]` Initializes/registers kernel devices or filesystems (`gpio_pin_register()`)
- `[stm32_ili9225.c:board_lcd_initialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[stm32_ili9225.c:board_lcd_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh nvmpg-stm32f1:dro && make`
