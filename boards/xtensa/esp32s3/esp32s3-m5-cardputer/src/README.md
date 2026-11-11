# `esp32s3-m5-cardputer/src` Component (`boards/xtensa/esp32s3/esp32s3-m5-cardputer/src`)

## Overview
Board-level C implementation (`src`) for `esp32s3-m5-cardputer` (`xtensa/esp32s3`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[esp32s3-m5-cardputer.h:esp32s3_bringup]` Public declaration `esp32s3_bringup()`
- `[esp32s3-m5-cardputer.h:board_i2c_init]` Public declaration `board_i2c_init()`
- `[esp32s3-m5-cardputer.h:esp32s3_kbd_initialize]` Public declaration `esp32s3_kbd_initialize()`
- `[esp32s3-m5-cardputer.h:DISPLAY_SPI]` Hardware/board configuration macros (`DISPLAY_SPI`, `DISPLAY_DC`, `DISPLAY_RST`, `DISPLAY_BCKL`)
- `[esp32s3_board_lcd_st7789.c:board_lcd_initialize]` Public function `board_lcd_initialize()`
- `[esp32s3_board_lcd_st7789.c:board_lcd_getdev]` Public function `board_lcd_getdev()`
- `[esp32s3_board_lcd_st7789.c:board_lcd_uninitialize]` Public function `board_lcd_uninitialize()`
- `[esp32s3_board_spi.c:esp32s3_spi2_status]` Public function `esp32s3_spi2_status()`
- `[esp32s3_board_spi.c:esp32s3_spi2_cmddata]` Public function `esp32s3_spi2_cmddata()`
- `[esp32s3_board_spi.c:esp32s3_spi3_cmddata]` Public function `esp32s3_spi3_cmddata()`
- `[esp32s3_board_spi.c:esp32s3_spi3_status]` Public function `esp32s3_spi3_status()`
- `[esp32s3_boot.c:esp32s3_board_initialize]` Public function `esp32s3_board_initialize()`
- `[esp32s3_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[esp32s3_bringup.c:esp32s3_bringup]` Public function `esp32s3_bringup()`
- `[esp32s3_kbd.c:esp32s3_kbd_initialize]` Public function `esp32s3_kbd_initialize()`
- `[esp32s3_reset.c:board_reset]` Public function `board_reset()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_BOARDCTL_RESET`, `CONFIG_ESP32S3_M5_CARDPUTER_KEYBOARD`, `CONFIG_ESP32S3_SPI`, `CONFIG_ESPRESSIF_HR_TIMER`, `CONFIG_LCD_ST7789`
- `[esp32s3_board_lcd_st7789.c:board_lcd_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32s3_board_spi.c:esp32s3_spi2_status]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32s3_kbd.c:esp32s3_kbd_initialize]` Validates preconditions and returns `-ENOMEM` on failure
- `[esp32s3_reset.c:#error]` Compile-time guard: `CONFIG_BOARD_ASSERT_RESET_VALUE must not be equal to EXIT_SUCCESS`

## Side Effects
- `[esp32s3_board_lcd_st7789.c:board_lcd_initialize]` Configures or drives hardware GPIO pins
- `[esp32s3_board_lcd_st7789.c:board_lcd_initialize]` Initializes/registers kernel devices or filesystems (`esp32s3_spibus_initialize()`)
- `[esp32s3_board_spi.c:esp32s3_spi2_status]` Configures or drives hardware GPIO pins
- `[esp32s3_bringup.c:esp32s3_bringup]` Initializes/registers kernel devices or filesystems (`board_lcd_initialize()`, `board_sdmmc_spi_initialize()`, `board_spidev_initialize()`, `esp32s3_ble_initialize()`, `esp32s3_kbd_initialize()`)
- `[esp32s3_kbd.c:esp32s3_kbd_initialize]` Configures or drives hardware GPIO pins
- `[esp32s3_kbd.c:esp32s3_kbd_initialize]` Initializes/registers kernel devices or filesystems (`keyboard_register()`)

## Verification
- Run: `./tools/configure.sh esp32s3-m5-cardputer:nsh && make`
