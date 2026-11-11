# `esp32s3-eye/src` Component (`boards/xtensa/esp32s3/esp32s3-eye/src`)

## Overview
Board-level C implementation (`src`) for `esp32s3-eye` (`xtensa/esp32s3`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[esp32s3-eye.h:esp32s3_bringup]` Public declaration `esp32s3_bringup()`
- `[esp32s3-eye.h:esp32s3_gpio_init]` Public declaration `esp32s3_gpio_init()`
- `[esp32s3-eye.h:board_spiflash_init]` Public declaration `board_spiflash_init()`
- `[esp32s3-eye.h:board_lcd_initialize]` Public declaration `board_lcd_initialize()`
- `[esp32s3-eye.h:board_lcd_getdev]` Public declaration `board_lcd_getdev()`
- `[esp32s3-eye.h:board_lcd_uninitialize]` Public declaration `board_lcd_uninitialize()`
- `[esp32s3-eye.h:board_i2c_init]` Public declaration `board_i2c_init()`
- `[esp32s3-eye.h:BUTTON_BOOT]` Hardware/board configuration macros (`BUTTON_BOOT`, `ESP32S3_EYE_DISPLAY_SPI`, `ESP32S3_EYE_DISPLAY_DC`, `ESP32S3_EYE_DISPLAY_BCKL`)
- `[esp32s3_board_lcd.c:board_lcd_initialize]` Public function `board_lcd_initialize()`
- `[esp32s3_board_lcd.c:board_lcd_getdev]` Public function `board_lcd_getdev()`
- `[esp32s3_board_lcd.c:board_lcd_uninitialize]` Public function `board_lcd_uninitialize()`
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
- `[esp32s3_gpio.c:esp32s3_gpio_init]` Public function `esp32s3_gpio_init()`
- `[esp32s3_reset.c:board_reset]` Public function `board_reset()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_BOARDCTL_RESET`, `CONFIG_DEV_GPIO`, `CONFIG_ESP32S3_EYE_LCD`, `CONFIG_ESP32S3_SPI`
- `[esp32s3_board_lcd.c:board_lcd_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32s3_board_spi.c:esp32s3_spi2_status]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32s3_gpio.c:DEBUGASSERT]` Requires `esp32s3gpio != NULL && value != NULL`
- `[esp32s3_gpio.c:DEBUGASSERT]` Requires `esp32s3gpio->id < BOARD_NGPIOOUT`
- `[esp32s3_gpio.c:DEBUGASSERT]` Requires `esp32s3gpio != NULL`
- `[esp32s3_gpio.c:#error]` Compile-time guard: `NGPIOINT is > 0 and GPIO interrupts aren't enabled`

## Side Effects
- `[esp32s3_board_lcd.c:board_lcd_initialize]` Configures or drives hardware GPIO pins
- `[esp32s3_board_lcd.c:board_lcd_initialize]` Initializes/registers kernel devices or filesystems (`esp32s3_spibus_initialize()`)
- `[esp32s3_board_spi.c:esp32s3_spi2_status]` Configures or drives hardware GPIO pins
- `[esp32s3_bringup.c:esp32s3_bringup]` Initializes/registers kernel devices or filesystems (`board_lcd_initialize()`, `board_sdmmc_initialize()`, `btn_lower_initialize()`, `esp32s3_ble_initialize()`, `fb_register()`)
- `[esp32s3_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[esp32s3_gpio.c:esp32s3_gpio_init]` Configures or drives hardware GPIO pins
- `[esp32s3_gpio.c:esp32s3_gpio_init]` Initializes/registers kernel devices or filesystems (`gpio_pin_register()`)

## Verification
- Run: `./tools/configure.sh esp32s3-eye:nsh && make`
