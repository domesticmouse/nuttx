# `lckfb-szpi-esp32s3/src` Component (`boards/xtensa/esp32s3/lckfb-szpi-esp32s3/src`)

## Overview
Board-level C implementation (`src`) for `lckfb-szpi-esp32s3` (`xtensa/esp32s3`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 11 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[esp32s3-szpi.h:esp32s3_bringup]` Public declaration `esp32s3_bringup()`
- `[esp32s3-szpi.h:esp32s3_gpio_init]` Public declaration `esp32s3_gpio_init()`
- `[esp32s3-szpi.h:board_spiflash_init]` Public declaration `board_spiflash_init()`
- `[esp32s3-szpi.h:board_i2c_init]` Public declaration `board_i2c_init()`
- `[esp32s3-szpi.h:board_i2sdev_initialize]` Public declaration `board_i2sdev_initialize()`
- `[esp32s3-szpi.h:esp_openeth_initialize]` Public declaration `esp_openeth_initialize()`
- `[esp32s3-szpi.h:esp32s3_pca9557_initialize]` Public declaration `esp32s3_pca9557_initialize()`
- `[esp32s3-szpi.h:esp32s3_ft5x06_initialize]` Public declaration `esp32s3_ft5x06_initialize()`
- `[esp32s3-szpi.h:esp32s3_qmi8658_initialize]` Public declaration `esp32s3_qmi8658_initialize()`
- `[esp32s3-szpi.h:esp32s3_camera_initialize]` Public declaration `esp32s3_camera_initialize()`
- `[esp32s3-szpi.h:esp32s3_es7210_initialize]` Public declaration `esp32s3_es7210_initialize()`
- `[esp32s3-szpi.h:GPIO_LCD_DC]` Hardware/board configuration macros (`GPIO_LCD_DC`, `GPIO_LCD_RST`, `SZPI_LCD_CS_PATH`, `SZPI_LCD_PWM_PATH`, `SZPI_LCD_PWM_FREQ`, `SZPI_LCD_PWM_DUTY` (+5 more))
- `[esp32s3_board_camera.c:esp32s3_camera_initialize]` Public function `esp32s3_camera_initialize()`
- `[esp32s3_board_es7210.c:esp32s3_es7210_initialize]` Public function `esp32s3_es7210_initialize()`
- `[esp32s3_board_lcd.c:board_lcd_initialize]` Public function `board_lcd_initialize()`
- `[esp32s3_board_lcd.c:board_lcd_getdev]` Public function `board_lcd_getdev()`
- `[esp32s3_board_lcd.c:board_lcd_uninitialize]` Public function `board_lcd_uninitialize()`
- `[esp32s3_board_spi.c:esp32s3_spi2_status]` Public function `esp32s3_spi2_status()`
- `[esp32s3_board_spi.c:esp32s3_spi2_cmddata]` Public function `esp32s3_spi2_cmddata()`
- `[esp32s3_board_spi.c:esp32s3_spi2_select]` Public function `esp32s3_spi2_select()`
- `[esp32s3_board_spi.c:esp32s3_spi3_status]` Public function `esp32s3_spi3_status()`
- `[esp32s3_board_spi.c:esp32s3_spi3_cmddata]` Public function `esp32s3_spi3_cmddata()`
- `[esp32s3_boot.c:esp32s3_board_initialize]` Public function `esp32s3_board_initialize()`
- *(+7 additional symbols across 11 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_AUDIO_ES7210`, `CONFIG_BOARDCTL_RESET`, `CONFIG_DEV_GPIO`, `CONFIG_ESP32S3_CAM`, `CONFIG_ESP32S3_SPI` (+3 more)
- `[esp32s3_board_camera.c:esp32s3_camera_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32s3_board_es7210.c:esp32s3_es7210_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32s3_board_lcd.c:board_lcd_initialize]` Validates preconditions and returns `-EIO`, `-ENODEV`, `-ENOTTY` on failure
- `[esp32s3_board_spi.c:esp32s3_spi2_status]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32s3_ft5x06.c:#error]` Compile-time guard: `Only support poll mode currently!`
- `[esp32s3_gpio.c:DEBUGASSERT]` Requires `esp32s3gpio != NULL && value != NULL`
- `[esp32s3_gpio.c:DEBUGASSERT]` Requires `esp32s3gpio->id < BOARD_NGPIOOUT`
- `[esp32s3_gpio.c:DEBUGASSERT]` Requires `esp32s3gpio != NULL`
- `[esp32s3_pca9557.c:esp32s3_pca9557_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[esp32s3_reset.c:#error]` Compile-time guard: `CONFIG_BOARD_ASSERT_RESET_VALUE must not be equal to EXIT_SUCCESS`

## Side Effects
- `[esp32s3_board_camera.c:esp32s3_camera_initialize]` Initializes/registers kernel devices or filesystems (`esp32s3_cam_initialize()`, `esp32s3_i2cbus_initialize()`, `gc0308_initialize()`, `imgdata_register()`, `imgsensor_register()`)
- `[esp32s3_board_es7210.c:esp32s3_es7210_initialize]` Initializes/registers kernel devices or filesystems (`audio_register()`, `es7210_initialize()`, `esp32s3_i2cbus_initialize()`, `esp_i2sbus_initialize()`)
- `[esp32s3_board_lcd.c:board_lcd_initialize]` Initializes/registers kernel devices or filesystems (`esp32s3_spibus_initialize()`)
- `[esp32s3_board_spi.c:esp32s3_spi2_status]` Configures or drives hardware GPIO pins
- `[esp32s3_bringup.c:esp32s3_bringup]` Initializes/registers kernel devices or filesystems (`board_capture_initialize()`, `board_i2sdev_initialize()`, `board_lcd_initialize()`, `board_motor_initialize()`, `board_pcnt_initialize()`)
- `[esp32s3_ft5x06.c:esp32s3_ft5x06_initialize]` Initializes/registers kernel devices or filesystems (`esp32s3_i2cbus_initialize()`, `ft5x06_register()`)
- `[esp32s3_gpio.c:esp32s3_gpio_init]` Configures or drives hardware GPIO pins
- `[esp32s3_gpio.c:esp32s3_gpio_init]` Initializes/registers kernel devices or filesystems (`gpio_pin_register()`)
- `[esp32s3_pca9557.c:esp32s3_pca9557_initialize]` Initializes/registers kernel devices or filesystems (`esp32s3_i2cbus_initialize()`, `pca9557_initialize()`)

## Verification
- Run: `./tools/configure.sh lckfb-szpi-esp32s3:nsh && make`
