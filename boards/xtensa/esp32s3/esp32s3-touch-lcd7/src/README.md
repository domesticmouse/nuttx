# `esp32s3-touch-lcd7/src` Component (`boards/xtensa/esp32s3/esp32s3-touch-lcd7/src`)

## Overview
Board-level C implementation (`src`) for `esp32s3-touch-lcd7` (`xtensa/esp32s3`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 6 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[esp32s3-touch-lcd7.h:esp32s3_bringup]` Public declaration `esp32s3_bringup()`
- `[esp32s3-touch-lcd7.h:board_ioexpander_initialize]` Public declaration `board_ioexpander_initialize()`
- `[esp32s3-touch-lcd7.h:board_lcd_initialize]` Public declaration `board_lcd_initialize()`
- `[esp32s3-touch-lcd7.h:BOARD_I2C_BUS]` Hardware/board configuration macros (`BOARD_I2C_BUS`, `BOARD_EXIO_TP_RST`, `BOARD_EXIO_DISP`, `BOARD_EXIO_LCD_RST`, `BOARD_EXIO_SD_CS`, `BOARD_EXIO_USB_SEL`)
- `[esp32s3_board_ioexpander.c:board_ioexpander_initialize]` Public function `board_ioexpander_initialize()`
- `[esp32s3_boot.c:esp32s3_board_initialize]` Public function `esp32s3_board_initialize()`
- `[esp32s3_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[esp32s3_bringup.c:esp32s3_bringup]` Public function `esp32s3_bringup()`
- `[esp32s3_lcd.c:board_lcd_initialize]` Public function `board_lcd_initialize()`
- `[esp32s3_reset.c:board_reset]` Public function `board_reset()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_BOARDCTL_RESET`, `CONFIG_ESP32S3_BOARD_LCD`, `CONFIG_IOEXPANDER_CH422G`
- `[esp32s3_lcd.c:board_lcd_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32s3_reset.c:#error]` Compile-time guard: `CONFIG_BOARD_ASSERT_RESET_VALUE must not be equal to EXIT_SUCCESS`

## Side Effects
- `[esp32s3_board_ioexpander.c:board_ioexpander_initialize]` Initializes/registers kernel devices or filesystems (`ch422g_initialize()`, `esp32s3_i2cbus_initialize()`)
- `[esp32s3_bringup.c:esp32s3_bringup]` Initializes/registers kernel devices or filesystems (`board_lcd_initialize()`, `nx_mount()`)
- `[esp32s3_lcd.c:board_lcd_initialize]` Initializes/registers kernel devices or filesystems (`board_ioexpander_initialize()`, `fb_register()`)

## Verification
- Run: `./tools/configure.sh esp32s3-touch-lcd7:lcd && make`
