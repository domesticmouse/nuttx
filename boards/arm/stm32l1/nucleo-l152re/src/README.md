# `nucleo-l152re/src` Component (`boards/arm/stm32l1/nucleo-l152re/src`)

## Overview
Board-level C implementation (`src`) for `nucleo-l152re` (`arm/stm32l1`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[nucleo-l152re.h:stm32_ili93418b_initialize]` Public declaration `stm32_ili93418b_initialize()`
- `[nucleo-l152re.h:stm32_spisd_initialize]` Public declaration `stm32_spisd_initialize()`
- `[nucleo-l152re.h:stm32_spiinitialize]` Public declaration `stm32_spiinitialize()`
- `[nucleo-l152re.h:GPIO_LED1]` Hardware/board configuration macros (`GPIO_LED1`, `LED_DRIVER_PATH`, `MIN_IRQBUTTON`, `MAX_IRQBUTTON`, `NUM_IRQBUTTONS`, `GPIO_BTN_USER` (+15 more))
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[stm32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[stm32_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[stm32_ili93418b.c:stm32_ili93418b_initialize]` Public function `stm32_ili93418b_initialize()`
- `[stm32_ili93418b.c:board_lcd_initialize]` Public function `board_lcd_initialize()`
- `[stm32_ili93418b.c:board_lcd_getdev]` Public function `board_lcd_getdev()`
- `[stm32_spi.c:stm32_spiinitialize]` Public function `stm32_spiinitialize()`
- `[stm32_spi.c:stm32_spi1select]` Public function `stm32_spi1select()`
- `[stm32_spi.c:stm32_spi1status]` Public function `stm32_spi1status()`
- `[stm32_spi.c:stm32_spi2select]` Public function `stm32_spi2select()`
- `[stm32_spi.c:stm32_spi2status]` Public function `stm32_spi2status()`
- `[stm32_spi.c:stm32_spi3select]` Public function `stm32_spi3select()`
- `[stm32_spi.c:stm32_spi3status]` Public function `stm32_spi3status()`
- `[stm32_spi.c:stm32_spi1cmddata]` Public function `stm32_spi1cmddata()`
- *(+7 additional symbols across 8 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_LCD_ILI9341`, `CONFIG_MMCSD_SPI`, `CONFIG_STM32_SPI`
- `[stm32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[stm32_spi.c:stm32_spiinitialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_spisd.c:#error]` Compile-time guard: `SD driver requires CONFIG_DISABLE_MOUNTPOINT to be disabled`

## Side Effects
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `stm32_common_initialize()`, `stm32_spisd_initialize()`, `userled_lower_initialize()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_ili93418b.c:stm32_ili93418b_initialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[stm32_ili93418b.c:stm32_ili93418b_initialize]` Configures or drives hardware GPIO pins
- `[stm32_ili93418b.c:stm32_ili93418b_initialize]` Initializes/registers kernel devices or filesystems (`ili9341_initialize()`, `stm32_gpio_initialize()`)
- `[stm32_spi.c:stm32_spiinitialize]` Configures or drives hardware GPIO pins
- `[stm32_spi.c:stm32_spiinitialize]` Initializes/registers kernel devices or filesystems (`spi_register()`, `stm32_spibus_initialize()`)
- `[stm32_spisd.c:stm32_spi1register]` Configures or drives hardware GPIO pins
- `[stm32_spisd.c:stm32_spi1register]` Initializes/registers kernel devices or filesystems (`stm32_spibus_initialize()`)
- `[stm32_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh nucleo-l152re:nsh && make`
