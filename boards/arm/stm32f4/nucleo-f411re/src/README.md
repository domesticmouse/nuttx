# `nucleo-f411re/src` Component (`boards/arm/stm32f4/nucleo-f411re/src`)

## Overview
Board-level C implementation (`src`) for `nucleo-f411re` (`arm/stm32f4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 11 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[nucleo-f411re.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[nucleo-f411re.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[nucleo-f411re.h:stm32_usbinitialize]` Public declaration `stm32_usbinitialize()`
- `[nucleo-f411re.h:stm32_adc_setup]` Public declaration `stm32_adc_setup()`
- `[nucleo-f411re.h:board_ajoy_initialize]` Public declaration `board_ajoy_initialize()`
- `[nucleo-f411re.h:stm32_mcp2515initialize]` Public declaration `stm32_mcp2515initialize()`
- `[nucleo-f411re.h:HAVE_MMCSD]` Hardware/board configuration macros (`HAVE_MMCSD`, `GPIO_LD2`, `MIN_IRQBUTTON`, `MAX_IRQBUTTON`, `NUM_IRQBUTTONS`, `GPIO_BTN_USER` (+31 more))
- `[stm32_adc.c:stm32_adc_setup]` Public function `stm32_adc_setup()`
- `[stm32_ajoystick.c:board_ajoy_initialize]` Public function `board_ajoy_initialize()`
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- `[stm32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[stm32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[stm32_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[stm32_lcd_ssd1306.c:board_lcd_initialize]` Public function `board_lcd_initialize()`
- `[stm32_lcd_ssd1306.c:board_lcd_getdev]` Public function `board_lcd_getdev()`
- `[stm32_lcd_ssd1306.c:board_lcd_uninitialize]` Public function `board_lcd_uninitialize()`
- `[stm32_mcp2515.c:mcp2515_interrupt]` Public function `mcp2515_interrupt()`
- `[stm32_mcp2515.c:stm32_mcp2515initialize]` Public function `stm32_mcp2515initialize()`
- *(+15 additional symbols across 11 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ADC`, `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_CAN_MCP2515`, `CONFIG_INPUT_AJOYSTICK` (+2 more)
- `[stm32_adc.c:stm32_adc_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_ajoystick.c:DEBUGASSERT]` Requires `g_ajoyhandler`
- `[stm32_ajoystick.c:#error]` Compile-time guard: `CONFIG_ADC is required for the Itead joystick`
- `[stm32_ajoystick.c:#error]` Compile-time guard: `CONFIG_STM32_ADC1 is required for Itead joystick`
- `[stm32_bringup.c:stm32_bringup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[stm32_mcp2515.c:DEBUGASSERT]` Requires `priv != NULL`
- `[stm32_userleds.c:DEBUGASSERT]` Requires `ret == OK`

## Side Effects
- `[stm32_adc.c:stm32_adc_setup]` Configures or drives hardware GPIO pins
- `[stm32_adc.c:stm32_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`)
- `[stm32_ajoystick.c:board_ajoy_initialize]` Configures or drives hardware GPIO pins
- `[stm32_ajoystick.c:board_ajoy_initialize]` Initializes/registers kernel devices or filesystems (`ajoy_register()`)
- `[stm32_ajoystick.c:board_ajoy_initialize]` Modifies interrupt controller or critical-section state
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `stm32_spidev_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Configures or drives hardware GPIO pins
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`board_ajoy_initialize()`, `board_lcd_initialize()`, `board_qencoder_initialize()`, `btn_lower_initialize()`, `fb_register()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_lcd_ssd1306.c:board_lcd_initialize]` Initializes/registers kernel devices or filesystems (`board_ssd1306_initialize()`)
- `[stm32_mcp2515.c:mcp2515_interrupt]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh nucleo-f411re:nsh && make`
