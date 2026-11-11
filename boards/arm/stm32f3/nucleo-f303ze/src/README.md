# `nucleo-f303ze/src` Component (`boards/arm/stm32f3/nucleo-f303ze/src`)

## Overview
Board-level C implementation (`src`) for `nucleo-f303ze` (`arm/stm32f3`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[nucleo-f303ze.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[nucleo-f303ze.h:stm32_adc_setup]` Public declaration `stm32_adc_setup()`
- `[nucleo-f303ze.h:GPIO_LD1]` Hardware/board configuration macros (`GPIO_LD1`, `GPIO_LD2`, `GPIO_LD3`, `GPIO_LED_GREEN`, `GPIO_LED_BLUE`, `GPIO_LED_RED` (+6 more))
- `[stm32_adc.c:stm32_adc_setup]` Public function `stm32_adc_setup()`
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- `[stm32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[stm32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[stm32_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[stm32_lcd.c:board_lcd_initialize]` Public function `board_lcd_initialize()`
- `[stm32_lcd.c:board_lcd_getdev]` Public function `board_lcd_getdev()`
- `[stm32_lcd.c:board_lcd_uninitialize]` Public function `board_lcd_uninitialize()`
- `[stm32_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[stm32_userleds.c:board_userled]` Public function `board_userled()`
- `[stm32_userleds.c:board_userled_all]` Public function `board_userled_all()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ADC`, `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_LCD_SSD1306`
- `[stm32_adc.c:stm32_adc_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure

## Side Effects
- `[stm32_adc.c:stm32_adc_setup]` Configures or drives hardware GPIO pins
- `[stm32_adc.c:stm32_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`)
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`stm32_common_initialize()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_lcd.c:board_lcd_initialize]` Initializes/registers kernel devices or filesystems (`board_ssd1306_initialize()`)
- `[stm32_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh nucleo-f303ze:nsh && make`
