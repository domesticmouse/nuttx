# `pinephone/src` Component (`boards/arm64/a64/pinephone/src`)

## Overview
Board-level C implementation (`src`) for `pinephone` (`arm64/a64`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 14 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[pinephone.h:pinephone_bringup]` Public declaration `pinephone_bringup()`
- `[pinephone.h:pinephone_led_initialize]` Public declaration `pinephone_led_initialize()`
- `[pinephone.h:LED1]` Hardware/board configuration macros (`LED1`, `LED2`, `LED3`)
- `[pinephone_display.h:pinephone_display_test_pattern]` Public declaration `pinephone_display_test_pattern()`
- `[pinephone_lcd.h:pinephone_lcd_backlight_enable]` Public declaration `pinephone_lcd_backlight_enable()`
- `[pinephone_lcd.h:pinephone_lcd_panel_reset]` Public declaration `pinephone_lcd_panel_reset()`
- `[pinephone_lcd.h:pinephone_lcd_panel_init]` Public declaration `pinephone_lcd_panel_init()`
- `[pinephone_lcd.h:PINEPHONE_LCD_PANEL_WIDTH]` Hardware/board configuration macros (`PINEPHONE_LCD_PANEL_WIDTH`, `PINEPHONE_LCD_PANEL_HEIGHT`)
- `[pinephone_pmic.h:pinephone_pmic_init]` Public declaration `pinephone_pmic_init()`
- `[pinephone_touch.h:pinephone_touch_panel_register]` Public declaration `pinephone_touch_panel_register()`
- `[pinephone_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[pinephone_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[pinephone_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[pinephone_boardinit.c:a64_memory_initialize]` Public function `a64_memory_initialize()`
- `[pinephone_boardinit.c:a64_board_initialize]` Public function `a64_board_initialize()`
- `[pinephone_boardinit.c:board_late_initialize]` Public function `board_late_initialize()`
- `[pinephone_bringup.c:pinephone_bringup]` Public function `pinephone_bringup()`
- `[pinephone_display.c:up_fbinitialize]` Public function `up_fbinitialize()`
- `[pinephone_display.c:up_fbgetvplane]` Public function `up_fbgetvplane()`
- `[pinephone_display.c:up_fbuninitialize]` Public function `up_fbuninitialize()`
- `[pinephone_display.c:pinephone_display_test_pattern]` Public function `pinephone_display_test_pattern()`
- `[pinephone_lcd.c:pinephone_lcd_backlight_enable]` Public function `pinephone_lcd_backlight_enable()`
- `[pinephone_lcd.c:pinephone_lcd_panel_reset]` Public function `pinephone_lcd_panel_reset()`
- *(+7 additional symbols across 14 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_LEDS`, `CONFIG_BOARDCTL_RESET`, `CONFIG_INPUT_GT9XX`, `CONFIG_USERLED`, `CONFIG_VIDEO_FB`
- `[pinephone_autoleds.c:DEBUGASSERT]` Requires `ret == OK`
- `[pinephone_display.c:DEBUGASSERT]` Requires `UI_CHANNELS == 1 || UI_CHANNELS == 3`
- `[pinephone_display.c:DEBUGASSERT]` Requires `g_pinephone_plane.xres_virtual == g_pinephone_video.xres`
- `[pinephone_display.c:DEBUGASSERT]` Requires `g_pinephone_plane.yres_virtual == g_pinephone_video.yres`
- `[pinephone_lcd.c:DEBUGASSERT]` Requires `len > 0`
- `[pinephone_lcd.c:DEBUGASSERT]` Requires `ret == len`
- `[pinephone_touch.c:DEBUGASSERT]` Requires `state != NULL && isr != NULL && arg != NULL`
- `[pinephone_touch.c:DEBUGASSERT]` Requires `state != NULL`
- `[pinephone_touch.c:DEBUGASSERT]` Requires `devpath != NULL && i2c != NULL`
- `[pinephone_userleds.c:DEBUGASSERT]` Requires `ret == OK`

## Side Effects
- `[pinephone_boardinit.c:a64_memory_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[pinephone_bringup.c:pinephone_bringup]` Initializes/registers kernel devices or filesystems (`a64_i2cbus_initialize()`, `fb_register()`, `i2c_register()`, `mpu60x0_register()`, `nx_mount()`)
- `[pinephone_lcd.c:pinephone_lcd_backlight_enable]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[pinephone_touch.c:pinephone_touch_panel_register]` Initializes/registers kernel devices or filesystems (`gt9xx_register()`)
- `[pinephone_touch.c:pinephone_touch_panel_register]` Modifies interrupt controller or critical-section state

## Verification
- Run: `./tools/configure.sh pinephone:nsh && make`
