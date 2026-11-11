# `common/src` Component (`boards/xtensa/esp32/common/src`)

## Overview
Board-level C implementation (`src`) for `common` (`xtensa/esp32`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 39 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[esp32_backlight.c:esp32_set_backlight]` Public function `esp32_set_backlight()`
- `[esp32_bme680.c:board_bme680_initialize]` Public function `board_bme680_initialize()`
- `[esp32_bmp180.c:board_bmp180_initialize]` Public function `board_bmp180_initialize()`
- `[esp32_bmp280.c:board_bmp280_initialize]` Public function `board_bmp280_initialize()`
- `[esp32_board_adc.c:board_adc_init]` Public function `board_adc_init()`
- `[esp32_board_apa102_lcd.c:board_lcd_initialize]` Public function `board_lcd_initialize()`
- `[esp32_board_apa102_lcd.c:board_lcd_getdev]` Public function `board_lcd_getdev()`
- `[esp32_board_apa102_lcd.c:board_lcd_uninitialize]` Public function `board_lcd_uninitialize()`
- `[esp32_board_apds9960.c:board_apds9960_initialize]` Public function `board_apds9960_initialize()`
- `[esp32_board_dac.c:board_dac_initialize]` Public function `board_dac_initialize()`
- `[esp32_board_i2c.c:esp32_i2c_register]` Public function `esp32_i2c_register()`
- `[esp32_board_i2sdev.c:board_i2sdev_initialize]` Public function `board_i2sdev_initialize()`
- `[esp32_board_mcpwm.c:board_motor_initialize]` Public function `board_motor_initialize()`
- `[esp32_board_mcpwm.c:board_capture_initialize]` Public function `board_capture_initialize()`
- `[esp32_board_pcnt.c:board_pcnt_initialize]` Public function `board_pcnt_initialize()`
- `[esp32_board_rmt.c:board_rmt_rxinitialize]` Public function `board_rmt_rxinitialize()`
- `[esp32_board_rmt.c:board_rmt_txinitialize]` Public function `board_rmt_txinitialize()`
- `[esp32_board_sdmmc.c:board_sdmmc_initialize]` Public function `board_sdmmc_initialize()`
- `[esp32_board_spi.c:esp32_spi2_status]` Public function `esp32_spi2_status()`
- `[esp32_board_spi.c:esp32_spi2_cmddata]` Public function `esp32_spi2_cmddata()`
- `[esp32_board_spi.c:esp32_spi3_status]` Public function `esp32_spi3_status()`
- `[esp32_board_spi.c:esp32_spi3_cmddata]` Public function `esp32_spi3_cmddata()`
- `[esp32_board_spidev.c:board_spidev_initialize]` Public function `board_spidev_initialize()`
- *(+36 additional symbols across 39 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BOARD_COMMON`, `CONFIG_AUDIO_CS4344`, `CONFIG_AUDIO_ES8388`, `CONFIG_CAN_MCP2515`, `CONFIG_DAC` (+35 more)
- `[esp32_bme680.c:board_bme680_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32_bmp180.c:board_bmp180_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32_bmp280.c:board_bmp280_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32_board_adc.c:board_adc_init]` Validates preconditions and returns `-ENODEV`, `-ENOMEM` on failure
- `[esp32_board_apa102_lcd.c:board_lcd_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32_board_apds9960.c:board_apds9960_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32_board_dac.c:board_dac_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32_board_i2sdev.c:board_i2sdev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32_board_mcpwm.c:board_motor_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32_board_rmt.c:board_rmt_rxinitialize]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32_board_sdmmc.c:board_sdmmc_initialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[esp32_backlight.c:esp32_set_backlight]` Configures or drives hardware GPIO pins
- `[esp32_bme680.c:board_bme680_initialize]` Initializes/registers kernel devices or filesystems (`bme680_register()`, `esp32_i2cbus_initialize()`)
- `[esp32_bmp180.c:board_bmp180_initialize]` Initializes/registers kernel devices or filesystems (`bmp180_register()`, `esp32_i2cbus_initialize()`)
- `[esp32_bmp280.c:board_bmp280_initialize]` Initializes/registers kernel devices or filesystems (`bmp280_register()`, `esp32_i2cbus_initialize()`)
- `[esp32_board_adc.c:board_adc_init]` Initializes/registers kernel devices or filesystems (`adc_register()`, `board_adc_register()`, `esp_adc_initialize()`)
- `[esp32_board_apa102_lcd.c:board_lcd_initialize]` Initializes/registers kernel devices or filesystems (`apa102_initialize()`, `esp32_spibus_initialize()`)
- `[esp32_board_apds9960.c:board_apds9960_initialize]` Configures or drives hardware GPIO pins
- `[esp32_board_apds9960.c:board_apds9960_initialize]` Initializes/registers kernel devices or filesystems (`apds9960_register()`, `esp32_i2cbus_initialize()`)
- `[esp32_board_apds9960.c:board_apds9960_initialize]` Modifies interrupt controller or critical-section state
- `[esp32_board_dac.c:board_dac_initialize]` Initializes/registers kernel devices or filesystems (`dac_register()`, `esp32_dac_initialize()`)
- `[esp32_board_i2c.c:esp32_i2c_register]` Initializes/registers kernel devices or filesystems (`esp32_i2cbus_initialize()`, `i2c_register()`)
- `[esp32_board_i2sdev.c:board_i2sdev_initialize]` Initializes/registers kernel devices or filesystems (`audio_i2s_initialize()`, `audio_register()`, `esp_i2sbus_initialize()`, `i2schar_register()`, `pcm_decode_initialize()`)

## Verification
- Run: `./tools/configure.sh sim:nsh && make`
