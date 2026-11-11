# `esp32s3-8048S043/src` Component (`boards/xtensa/esp32s3/esp32s3-8048S043/src`)

## Overview
Board-level C implementation (`src`) for `esp32s3-8048S043` (`xtensa/esp32s3`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 9 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[esp32s3-8048S043.h:esp32s3_bringup]` Public declaration `esp32s3_bringup()`
- `[esp32s3-8048S043.h:esp32s3_gpio_init]` Public declaration `esp32s3_gpio_init()`
- `[esp32s3-8048S043.h:board_spiflash_init]` Public declaration `board_spiflash_init()`
- `[esp32s3-8048S043.h:board_i2c_init]` Public declaration `board_i2c_init()`
- `[esp32s3-8048S043.h:board_touchscreen_initialize]` Public declaration `board_touchscreen_initialize()`
- `[esp32s3-8048S043.h:board_lcd_initialize]` Public declaration `board_lcd_initialize()`
- `[esp32s3-8048S043.h:TOUCHSCEEN_I2C]` Hardware/board configuration macros (`TOUCHSCEEN_I2C`, `TOUCHSCEEN_ADDR`, `TOUCHSCEEN_CLOCK`, `TOUCHSCEEN_INT`, `ESP32S3_DISPLAY_BCKL`, `BUTTON_BOOT`)
- `[esp32s3_board_spi.c:esp32s3_spi2_status]` Public function `esp32s3_spi2_status()`
- `[esp32s3_board_spi.c:esp32s3_spi3_status]` Public function `esp32s3_spi3_status()`
- `[esp32s3_board_touchsceen.c:board_touchscreen_initialize]` Public function `board_touchscreen_initialize()`
- `[esp32s3_boot.c:esp32s3_board_initialize]` Public function `esp32s3_board_initialize()`
- `[esp32s3_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[esp32s3_bringup.c:esp32s3_bringup]` Public function `esp32s3_bringup()`
- `[esp32s3_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[esp32s3_buttons.c:board_buttons]` Public function `board_buttons()`
- `[esp32s3_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[esp32s3_gpio.c:esp32s3_gpio_init]` Public function `esp32s3_gpio_init()`
- `[esp32s3_lcd.c:board_lcd_initialize]` Public function `board_lcd_initialize()`
- `[esp32s3_reset.c:board_reset]` Public function `board_reset()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_BOARDCTL_RESET`, `CONFIG_DEV_GPIO`, `CONFIG_ESP32S3_BOARD_LCD`, `CONFIG_ESP32S3_BOARD_TOUCHSCREEN` (+1 more)
- `[esp32s3_board_touchsceen.c:DEBUGASSERT]` Requires `dev && dev->i2c && buf`
- `[esp32s3_board_touchsceen.c:DEBUGASSERT]` Requires `dev && dev->i2c`
- `[esp32s3_gpio.c:DEBUGASSERT]` Requires `esp32s3gpio != NULL && value != NULL`
- `[esp32s3_gpio.c:DEBUGASSERT]` Requires `esp32s3gpio->id < BOARD_NGPIOOUT`
- `[esp32s3_gpio.c:DEBUGASSERT]` Requires `esp32s3gpio != NULL`
- `[esp32s3_gpio.c:#error]` Compile-time guard: `NGPIOINT is > 0 and GPIO interrupts aren't enabled`
- `[esp32s3_reset.c:#error]` Compile-time guard: `CONFIG_BOARD_ASSERT_RESET_VALUE must not be equal to EXIT_SUCCESS`

## Side Effects
- `[esp32s3_board_touchsceen.c:board_touchscreen_initialize]` Initializes/registers kernel devices or filesystems (`esp32s3_i2cbus_initialize()`, `touch_register()`)
- `[esp32s3_bringup.c:esp32s3_bringup]` Initializes/registers kernel devices or filesystems (`board_lcd_initialize()`, `board_sdmmc_initialize()`, `board_spidev_initialize()`, `board_touchscreen_initialize()`, `btn_lower_initialize()`)
- `[esp32s3_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[esp32s3_gpio.c:esp32s3_gpio_init]` Configures or drives hardware GPIO pins
- `[esp32s3_gpio.c:esp32s3_gpio_init]` Initializes/registers kernel devices or filesystems (`gpio_pin_register()`)
- `[esp32s3_lcd.c:board_lcd_initialize]` Configures or drives hardware GPIO pins
- `[esp32s3_lcd.c:board_lcd_initialize]` Initializes/registers kernel devices or filesystems (`fb_register()`)

## Verification
- Run: `./tools/configure.sh esp32s3-8048S043:nsh && make`
