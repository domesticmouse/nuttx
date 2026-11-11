# `b-l072z-lrwan1/src` Component (`boards/arm/stm32l0/b-l072z-lrwan1/src`)

## Overview
Board-level C implementation (`src`) for `b-l072z-lrwan1` (`arm/stm32l0`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[b-l072z-lrwan1.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[b-l072z-lrwan1.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[b-l072z-lrwan1.h:stm32_lpwaninitialize]` Public declaration `stm32_lpwaninitialize()`
- `[b-l072z-lrwan1.h:stm32_adc_setup]` Public declaration `stm32_adc_setup()`
- `[b-l072z-lrwan1.h:GPIO_LED1]` Hardware/board configuration macros (`GPIO_LED1`, `GPIO_LED2`, `GPIO_LED3`, `GPIO_LED4`, `LED_DRIVER_PATH`, `MIN_IRQBUTTON` (+11 more))
- `[stm32_adc.c:stm32_adc_setup]` Public function `stm32_adc_setup()`
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- `[stm32_lcd_ssd1306.c:board_lcd_initialize]` Public function `board_lcd_initialize()`
- `[stm32_lcd_ssd1306.c:board_lcd_getdev]` Public function `board_lcd_getdev()`
- `[stm32_lcd_ssd1306.c:board_lcd_uninitialize]` Public function `board_lcd_uninitialize()`
- `[stm32_spi.c:stm32_spidev_initialize]` Public function `stm32_spidev_initialize()`
- `[stm32_spi.c:stm32_spi1select]` Public function `stm32_spi1select()`
- `[stm32_spi.c:stm32_spi1status]` Public function `stm32_spi1status()`
- `[stm32_spi.c:stm32_spi2select]` Public function `stm32_spi2select()`
- `[stm32_spi.c:stm32_spi2status]` Public function `stm32_spi2status()`
- `[stm32_sx127x.c:stm32_lpwaninitialize]` Public function `stm32_lpwaninitialize()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ADC`, `CONFIG_ARCH`, `CONFIG_ARCH_LEDS`, `CONFIG_LCD_SSD1306`, `CONFIG_LPWAN_SX127X`, `CONFIG_STM32_SPI`
- `[stm32_adc.c:stm32_adc_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_sx127x.c:stm32_lpwaninitialize]` Validates preconditions and returns `-EINVAL`, `-ENODEV` on failure

## Side Effects
- `[stm32_adc.c:stm32_adc_setup]` Configures or drives hardware GPIO pins
- `[stm32_adc.c:stm32_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`)
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `stm32_spidev_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`i2c_register()`, `stm32_i2c_register()`, `stm32_i2cbus_initialize()`, `userled_lower_initialize()`)
- `[stm32_lcd_ssd1306.c:board_lcd_initialize]` Initializes/registers kernel devices or filesystems (`board_ssd1306_initialize()`)
- `[stm32_spi.c:stm32_spidev_initialize]` Configures or drives hardware GPIO pins
- `[stm32_sx127x.c:stm32_lpwaninitialize]` Configures or drives hardware GPIO pins
- `[stm32_sx127x.c:stm32_lpwaninitialize]` Initializes/registers kernel devices or filesystems (`stm32_spibus_initialize()`, `sx127x_register()`)

## Verification
- Run: `./tools/configure.sh b-l072z-lrwan1:nsh && make`
