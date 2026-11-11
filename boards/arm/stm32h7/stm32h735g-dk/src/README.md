# `stm32h735g-dk/src` Component (`boards/arm/stm32h7/stm32h735g-dk/src`)

## Overview
Board-level C implementation (`src`) for `stm32h735g-dk` (`arm/stm32h7`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 10 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[stm32h735g-dk.h:stm32_hyperram_initialize]` Public declaration `stm32_hyperram_initialize()`
- `[stm32h735g-dk.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[stm32h735g-dk.h:stm32_tsc_setup]` Public declaration `stm32_tsc_setup()`
- `[stm32h735g-dk.h:stm32_can_setup]` Public declaration `stm32_can_setup()`
- `[stm32h735g-dk.h:GPIO_LED_GREEN]` Hardware/board configuration macros (`GPIO_LED_GREEN`, `GPIO_LED_RED`, `GPIO_BTN_USER`, `GPIO_LCD_DISP`, `GPIO_LCD_BL`, `GPIO_TOUCH_INT`)
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- `[stm32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[stm32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[stm32_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[stm32_can.c:stm32_can_setup]` Public function `stm32_can_setup()`
- `[stm32_hyperram.c:stm32_hyperram_initialize]` Public function `stm32_hyperram_initialize()`
- `[stm32_lcd.c:up_fbinitialize]` Public function `up_fbinitialize()`
- `[stm32_lcd.c:up_fbgetvplane]` Public function `up_fbgetvplane()`
- `[stm32_lcd.c:up_fbuninitialize]` Public function `up_fbuninitialize()`
- `[stm32_touchscreen.c:stm32_tsc_setup]` Public function `stm32_tsc_setup()`
- `[stm32_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[stm32_userleds.c:board_userled]` Public function `board_userled()`
- `[stm32_userleds.c:board_userled_all]` Public function `board_userled_all()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_INPUT_GT9XX`, `CONFIG_STM32_FDCAN_CHARDRIVER`, `CONFIG_STM32_LTDC`
- `[stm32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[stm32_can.c:stm32_can_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_lcd.c:#error]` Compile-time guard: `The LCD framebuffer must reside in HyperRAM`
- `[stm32_touchscreen.c:#error]` Compile-time guard: `The touchscreen requires CONFIG_STM32_I2C4`

## Side Effects
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`btn_lower_initialize()`, `fb_register()`, `nx_mount()`, `userled_lower_initialize()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_can.c:stm32_can_setup]` Initializes/registers kernel devices or filesystems (`can_register()`)
- `[stm32_hyperram.c:stm32_hyperram_initialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[stm32_hyperram.c:stm32_hyperram_initialize]` Configures or drives hardware GPIO pins
- `[stm32_lcd.c:up_fbinitialize]` Configures or drives hardware GPIO pins
- `[stm32_lcd.c:up_fbinitialize]` Initializes/registers kernel devices or filesystems (`stm32_hyperram_initialize()`)
- `[stm32_touchscreen.c:stm32_tsc_setup]` Configures or drives hardware GPIO pins
- `[stm32_touchscreen.c:stm32_tsc_setup]` Initializes/registers kernel devices or filesystems (`gt9xx_register()`, `stm32_i2cbus_initialize()`)
- `[stm32_touchscreen.c:stm32_tsc_setup]` Modifies interrupt controller or critical-section state

## Verification
- Run: `./tools/configure.sh stm32h735g-dk:nsh && make`
