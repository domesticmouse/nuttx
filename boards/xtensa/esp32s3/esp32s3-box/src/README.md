# `esp32s3-box/src` Component (`boards/xtensa/esp32s3/esp32s3-box/src`)

## Overview
Board-level C implementation (`src`) for `esp32s3-box` (`xtensa/esp32s3`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 10 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[esp32s3-box.h:esp32s3_bringup]` Public declaration `esp32s3_bringup()`
- `[esp32s3-box.h:board_spiflash_init]` Public declaration `board_spiflash_init()`
- `[esp32s3-box.h:board_lcd_initialize]` Public declaration `board_lcd_initialize()`
- `[esp32s3-box.h:board_lcd_getdev]` Public declaration `board_lcd_getdev()`
- `[esp32s3-box.h:board_lcd_uninitialize]` Public declaration `board_lcd_uninitialize()`
- `[esp32s3-box.h:board_touchscreen_initialize]` Public declaration `board_touchscreen_initialize()`
- `[esp32s3-box.h:BUTTON_BOOT]` Hardware/board configuration macros (`BUTTON_BOOT`, `DISPLAY_SPI`, `DISPLAY_DC`, `DISPLAY_BCKL`, `DISPLAY_RST`, `TOUCHSCEEN_I2C` (+3 more))
- `[esp32s3_board_lcd_ili9342c.c:board_lcd_initialize]` Public function `board_lcd_initialize()`
- `[esp32s3_board_lcd_ili9342c.c:board_lcd_getdev]` Public function `board_lcd_getdev()`
- `[esp32s3_board_lcd_ili9342c.c:board_lcd_uninitialize]` Public function `board_lcd_uninitialize()`
- `[esp32s3_board_lcd_st7789.c:board_lcd_initialize]` Public function `board_lcd_initialize()`
- `[esp32s3_board_lcd_st7789.c:board_lcd_getdev]` Public function `board_lcd_getdev()`
- `[esp32s3_board_lcd_st7789.c:board_lcd_uninitialize]` Public function `board_lcd_uninitialize()`
- `[esp32s3_board_spi.c:esp32s3_spi2_status]` Public function `esp32s3_spi2_status()`
- `[esp32s3_board_spi.c:esp32s3_spi2_cmddata]` Public function `esp32s3_spi2_cmddata()`
- `[esp32s3_board_spi.c:esp32s3_spi3_status]` Public function `esp32s3_spi3_status()`
- `[esp32s3_board_spi.c:esp32s3_spi3_cmddata]` Public function `esp32s3_spi3_cmddata()`
- `[esp32s3_board_touchsceen_gt911.c:board_touchscreen_initialize]` Public function `board_touchscreen_initialize()`
- `[esp32s3_board_touchsceen_tt21100.c:board_touchscreen_initialize]` Public function `board_touchscreen_initialize()`
- `[esp32s3_boot.c:esp32s3_board_initialize]` Public function `esp32s3_board_initialize()`
- `[esp32s3_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[esp32s3_bringup.c:esp32s3_bringup]` Public function `esp32s3_bringup()`
- `[esp32s3_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[esp32s3_buttons.c:board_buttons]` Public function `board_buttons()`
- *(+2 additional symbols across 10 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_BOARDCTL_RESET`, `CONFIG_ESP32S3_BOARD_TOUCHSCREEN`, `CONFIG_ESP32S3_BOX_LCD`, `CONFIG_ESP32S3_SPI` (+1 more)
- `[esp32s3_board_lcd_ili9342c.c:board_lcd_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32s3_board_lcd_st7789.c:board_lcd_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32s3_board_spi.c:esp32s3_spi2_status]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32s3_board_touchsceen_gt911.c:DEBUGASSERT]` Requires `dev && dev->i2c && buf`
- `[esp32s3_board_touchsceen_gt911.c:DEBUGASSERT]` Requires `dev && dev->i2c`
- `[esp32s3_board_touchsceen_tt21100.c:board_touchscreen_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32s3_reset.c:#error]` Compile-time guard: `CONFIG_BOARD_ASSERT_RESET_VALUE must not be equal to EXIT_SUCCESS`

## Side Effects
- `[esp32s3_board_lcd_ili9342c.c:board_lcd_initialize]` Configures or drives hardware GPIO pins
- `[esp32s3_board_lcd_ili9342c.c:board_lcd_initialize]` Initializes/registers kernel devices or filesystems (`esp32s3_spibus_initialize()`, `ili9341_initialize()`)
- `[esp32s3_board_lcd_st7789.c:board_lcd_initialize]` Configures or drives hardware GPIO pins
- `[esp32s3_board_lcd_st7789.c:board_lcd_initialize]` Initializes/registers kernel devices or filesystems (`esp32s3_spibus_initialize()`)
- `[esp32s3_board_spi.c:esp32s3_spi2_status]` Configures or drives hardware GPIO pins
- `[esp32s3_board_touchsceen_gt911.c:board_touchscreen_initialize]` Initializes/registers kernel devices or filesystems (`esp32s3_i2cbus_initialize()`, `touch_register()`)
- `[esp32s3_board_touchsceen_tt21100.c:board_touchscreen_initialize]` Initializes/registers kernel devices or filesystems (`esp32s3_i2cbus_initialize()`, `touch_register()`)
- `[esp32s3_bringup.c:esp32s3_bringup]` Initializes/registers kernel devices or filesystems (`board_lcd_initialize()`, `board_touchscreen_initialize()`, `btn_lower_initialize()`, `esp32s3_ble_initialize()`, `esp_efuse_initialize()`)
- `[esp32s3_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh esp32s3-box:nsh && make`
