# `esp32s3-lcd-ev/src` Component (`boards/xtensa/esp32s3/esp32s3-lcd-ev/src`)

## Overview
Board-level C implementation (`src`) for `esp32s3-lcd-ev` (`xtensa/esp32s3`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 10 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[esp32s3-lcd-ev.h:esp32s3_bringup]` Public declaration `esp32s3_bringup()`
- `[esp32s3-lcd-ev.h:board_spiflash_init]` Public declaration `board_spiflash_init()`
- `[esp32s3-lcd-ev.h:board_ws2812_initialize]` Public declaration `board_ws2812_initialize()`
- `[esp32s3-lcd-ev.h:board_lcd_initialize]` Public declaration `board_lcd_initialize()`
- `[esp32s3-lcd-ev.h:board_touchscreen_initialize]` Public declaration `board_touchscreen_initialize()`
- `[esp32s3-lcd-ev.h:board_ioexpander_set_pin]` Public declaration `board_ioexpander_set_pin()`
- `[esp32s3-lcd-ev.h:board_ioexpander_output]` Public declaration `board_ioexpander_output()`
- `[esp32s3-lcd-ev.h:board_ioexpander_initialize]` Public declaration `board_ioexpander_initialize()`
- `[esp32s3-lcd-ev.h:esp32s3_es8311_initialize]` Public declaration `esp32s3_es8311_initialize()`
- `[esp32s3-lcd-ev.h:BUTTON_BOOT]` Hardware/board configuration macros (`BUTTON_BOOT`, `I2C_PORT`, `SPEAKER_ENABLE_GPIO`)
- `[esp32s3_board_spi.c:esp32s3_spi2_status]` Public function `esp32s3_spi2_status()`
- `[esp32s3_board_spi.c:esp32s3_spi2_cmddata]` Public function `esp32s3_spi2_cmddata()`
- `[esp32s3_board_spi.c:esp32s3_spi3_status]` Public function `esp32s3_spi3_status()`
- `[esp32s3_board_spi.c:esp32s3_spi3_cmddata]` Public function `esp32s3_spi3_cmddata()`
- `[esp32s3_boot.c:esp32s3_board_initialize]` Public function `esp32s3_board_initialize()`
- `[esp32s3_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[esp32s3_bringup.c:esp32s3_bringup]` Public function `esp32s3_bringup()`
- `[esp32s3_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[esp32s3_buttons.c:board_buttons]` Public function `board_buttons()`
- `[esp32s3_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[esp32s3_ioexpander.c:board_ioexpander_set_pin]` Public function `board_ioexpander_set_pin()`
- `[esp32s3_ioexpander.c:board_ioexpander_output]` Public function `board_ioexpander_output()`
- `[esp32s3_ioexpander.c:board_ioexpander_initialize]` Public function `board_ioexpander_initialize()`
- `[esp32s3_lcd.c:esp_rom_delay_us]` Public function `esp_rom_delay_us()`
- *(+4 additional symbols across 10 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_BOARDCTL_RESET`, `CONFIG_ESP32S3_BOARD_IOEXPANDER`, `CONFIG_ESP32S3_BOARD_LCD`, `CONFIG_ESP32S3_BOARD_TOUCHPAD` (+2 more)
- `[esp32s3_board_spi.c:esp32s3_spi2_status]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32s3_bringup.c:esp32s3_bringup]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32s3_ioexpander.c:DEBUGASSERT]` Requires `pin < 8`
- `[esp32s3_lcd.c:DEBUGASSERT]` Requires `board_ioexpander_output(CS_PIN, v ? 1 : 0) == 0`
- `[esp32s3_lcd.c:DEBUGASSERT]` Requires `board_ioexpander_output(SCK_PIN, v ? 1 : 0) == 0`
- `[esp32s3_lcd.c:DEBUGASSERT]` Requires `board_ioexpander_output(SDO_PIN, v ? 1 : 0) == 0`
- `[esp32s3_reset.c:#error]` Compile-time guard: `CONFIG_BOARD_ASSERT_RESET_VALUE must not be equal to EXIT_SUCCESS`
- `[esp32s3_touchscreen.c:board_touchscreen_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[esp32s3_ws2812.c:board_ws2812_initialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[esp32s3_board_spi.c:esp32s3_spi2_status]` Configures or drives hardware GPIO pins
- `[esp32s3_bringup.c:esp32s3_bringup]` Configures or drives hardware GPIO pins
- `[esp32s3_bringup.c:esp32s3_bringup]` Initializes/registers kernel devices or filesystems (`board_i2sdev_initialize()`, `board_lcd_initialize()`, `board_touchscreen_initialize()`, `board_ws2812_initialize()`, `btn_lower_initialize()`)
- `[esp32s3_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[esp32s3_ioexpander.c:board_ioexpander_set_pin]` Initializes/registers kernel devices or filesystems (`esp32s3_i2cbus_initialize()`)
- `[esp32s3_lcd.c:esp_rom_delay_us]` Configures or drives hardware GPIO pins
- `[esp32s3_lcd.c:esp_rom_delay_us]` Initializes/registers kernel devices or filesystems (`board_ioexpander_initialize()`, `fb_register()`)
- `[esp32s3_touchscreen.c:board_touchscreen_initialize]` Initializes/registers kernel devices or filesystems (`esp32s3_i2cbus_initialize()`, `ft5x06_register()`)
- `[esp32s3_ws2812.c:board_ws2812_initialize]` Initializes/registers kernel devices or filesystems (`esp32s3_spibus_initialize()`, `ws2812_leds_register()`)

## Verification
- Run: `./tools/configure.sh esp32s3-lcd-ev:nsh && make`
