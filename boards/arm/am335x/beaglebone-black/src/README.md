# `beaglebone-black/src` Component (`boards/arm/am335x/beaglebone-black/src`)

## Overview
Board-level C implementation (`src`) for `beaglebone-black` (`arm/am335x`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 6 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[beaglebone-black.h:am335x_bringup]` Public declaration `am335x_bringup()`
- `[beaglebone-black.h:am335x_led_initialize]` Public declaration `am335x_led_initialize()`
- `[beaglebone-black.h:HAVE_LCD]` Hardware/board configuration macros (`HAVE_LCD`, `HAVE_TDA19988`, `CONFIG_BEAGLEBONE_VIDEOMODE`, `TDA19988_I2CBUS`, `TDA19988_HDMI_I2CADDR`, `TDA19988_CEC_I2CADDR` (+5 more))
- `[am335x_boot.c:am335x_memory_initialize]` Public function `am335x_memory_initialize()`
- `[am335x_boot.c:am335x_board_initialize]` Public function `am335x_board_initialize()`
- `[am335x_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[am335x_bringup.c:am335x_bringup]` Public function `am335x_bringup()`
- `[am335x_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[am335x_buttons.c:board_buttons]` Public function `board_buttons()`
- `[am335x_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[am335x_lcd.c:up_fbinitialize]` Public function `up_fbinitialize()`
- `[am335x_leds.c:am335x_led_initialize]` Public function `am335x_led_initialize()`
- `[am335x_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[am335x_leds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[am335x_leds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[am335x_leds.c:board_userled]` Public function `board_userled()`
- `[am335x_leds.c:board_userled_all]` Public function `board_userled_all()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_AM335X_LCDC`, `CONFIG_ARCH_BUTTONS`
- `[am335x_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[am335x_lcd.c:up_fbinitialize]` Validates preconditions and returns `-ENOSYS`, `-ENOTSUP` on failure

## Side Effects
- `[am335x_boot.c:am335x_memory_initialize]` Initializes/registers kernel devices or filesystems (`am335x_led_initialize()`)
- `[am335x_bringup.c:am335x_bringup]` Initializes/registers kernel devices or filesystems (`am335x_can_initialize()`, `am335x_can_register()`, `am335x_i2c_register()`, `am335x_i2cbus_initialize()`, `can_register()`)
- `[am335x_buttons.c:board_button_initialize]` Modifies interrupt controller or critical-section state
- `[am335x_lcd.c:up_fbinitialize]` Initializes/registers kernel devices or filesystems (`am335x_lcd_initialize()`)

## Verification
- Run: `./tools/configure.sh beaglebone-black:nsh && make`
