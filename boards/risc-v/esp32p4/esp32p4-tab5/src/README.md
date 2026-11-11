# `esp32p4-tab5/src` Component (`boards/risc-v/esp32p4/esp32p4-tab5/src`)

## Overview
Board-level C implementation (`src`) for `esp32p4-tab5` (`risc-v/esp32p4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 18 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[esp32p4-tab5.h:esp_bringup]` Public declaration `esp_bringup()`
- `[esp32p4-tab5.h:esp_gpio_init]` Public declaration `esp_gpio_init()`
- `[esp32p4-tab5.h:tab5_mipi_phy_power]` Public declaration `tab5_mipi_phy_power()`
- `[esp32p4-tab5.h:tab5_lcd_enable]` Public declaration `tab5_lcd_enable()`
- `[esp32p4-tab5.h:tab5_lcd_backlight]` Public declaration `tab5_lcd_backlight()`
- `[esp32p4-tab5.h:tab5_lcd_power_init]` Public declaration `tab5_lcd_power_init()`
- `[esp32p4-tab5.h:tab5_fb_reload_test_pattern]` Public declaration `tab5_fb_reload_test_pattern()`
- `[esp32p4-tab5.h:tab5_mipi_dsi_dpi_config]` Public declaration `tab5_mipi_dsi_dpi_config()`
- `[esp32p4-tab5.h:tab5_pi4ioe_init]` Public declaration `tab5_pi4ioe_init()`
- `[esp32p4-tab5.h:tab5_pi4ioe_high_write_pin]` Public declaration `tab5_pi4ioe_high_write_pin()`
- `[esp32p4-tab5.h:tab5_pi4ioe_low_write_pin]` Public declaration `tab5_pi4ioe_low_write_pin()`
- `[esp32p4-tab5.h:tab5_touchscreen_power_init]` Public declaration `tab5_touchscreen_power_init()`
- `[esp32p4-tab5.h:tab5_touchscreen_init]` Public declaration `tab5_touchscreen_init()`
- `[esp32p4-tab5.h:tab5_sd_card_power]` Public declaration `tab5_sd_card_power()`
- `[esp32p4_lcd_ili9881c.h:tab5_ili9881c_initialize]` Public declaration `tab5_ili9881c_initialize()`
- `[esp32p4_lcd_st7121.h:tab5_st7121_initialize]` Public declaration `tab5_st7121_initialize()`
- `[esp32p4_lcd_st7123.h:tab5_st7123_initialize]` Public declaration `tab5_st7123_initialize()`
- `[esp32p4_boot.c:esp_board_initialize]` Public function `esp_board_initialize()`
- `[esp32p4_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[esp32p4_bringup.c:esp_bringup]` Public function `esp_bringup()`
- `[esp32p4_display.c:up_fbinitialize]` Public function `up_fbinitialize()`
- `[esp32p4_display.c:up_fbgetvplane]` Public function `up_fbgetvplane()`
- `[esp32p4_display.c:up_fbuninitialize]` Public function `up_fbuninitialize()`
- *(+18 additional symbols across 18 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_BOARDCTL`, `CONFIG_BOARDCTL_RESET`, `CONFIG_DEV_GPIO`, `CONFIG_ESP32P4_TAB5_HMI_POWER`, `CONFIG_ESP32P4_TAB5_IOEXPANDER` (+8 more)
- `[esp32p4_display.c:DEBUGASSERT]` Requires `vtable != NULL && vtable == &g_tab5_vtable && vinfo != NULL`
- `[esp32p4_display.c:DEBUGASSERT]` Requires `vtable != NULL && vtable == &g_tab5_vtable && pinfo != NULL`
- `[esp32p4_display.c:DEBUGASSERT]` Requires `vtable != NULL && vtable == &g_tab5_vtable`
- `[esp32p4_gpio.c:DEBUGASSERT]` Requires `espgpio != NULL && value != NULL`
- `[esp32p4_gpio.c:DEBUGASSERT]` Requires `espgpio->id < BOARD_NGPIOOUT`
- `[esp32p4_gpio.c:DEBUGASSERT]` Requires `espgpio != NULL`
- `[esp32p4_gpio.c:#error]` Compile-time guard: `NGPIOINT is > 0 and GPIO interrupts aren't enabled`
- `[esp32p4_ioexpander.c:tab5_pi4ioe_init]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32p4_mipi_dpi.c:DEBUGASSERT]` Requires `cfg != NULL`
- `[esp32p4_touch_gt911.c:tab5_touchscreen_init]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32p4_touch_st7123.c:tab5_touchscreen_init]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[esp32p4_bringup.c:esp_bringup]` Initializes/registers kernel devices or filesystems (`esp_mipi_dsi_initialize()`, `esp_mmcsd_spi_initialize()`, `fb_register()`, `nx_mount()`)
- `[esp32p4_display.c:up_fbinitialize]` Initializes/registers kernel devices or filesystems (`tab5_panel_initialize()`)
- `[esp32p4_gpio.c:esp_gpio_init]` Configures or drives hardware GPIO pins
- `[esp32p4_gpio.c:esp_gpio_init]` Initializes/registers kernel devices or filesystems (`gpio_pin_register()`)
- `[esp32p4_hmi_power.c:tab5_touchscreen_power_init]` Configures or drives hardware GPIO pins
- `[esp32p4_ioexpander.c:tab5_pi4ioe_init]` Initializes/registers kernel devices or filesystems (`esp_i2cbus_initialize()`, `pi4ioe5v6408_initialize()`)
- `[esp32p4_lcd_ili9881c.c:tab5_ili9881c_initialize]` Initializes/registers kernel devices or filesystems (`mipi_dsi_device_register()`)
- `[esp32p4_lcd_st7121.c:tab5_st7121_initialize]` Initializes/registers kernel devices or filesystems (`mipi_dsi_device_register()`)
- `[esp32p4_lcd_st7123.c:tab5_st7123_initialize]` Initializes/registers kernel devices or filesystems (`mipi_dsi_device_register()`)
- `[esp32p4_touch_gt911.c:tab5_touchscreen_init]` Configures or drives hardware GPIO pins
- `[esp32p4_touch_gt911.c:tab5_touchscreen_init]` Initializes/registers kernel devices or filesystems (`esp_i2cbus_initialize()`, `gt9xx_register()`)
- `[esp32p4_touch_gt911.c:tab5_touchscreen_init]` Modifies interrupt controller or critical-section state

## Verification
- Run: `./tools/configure.sh esp32p4-tab5:nsh && make`
