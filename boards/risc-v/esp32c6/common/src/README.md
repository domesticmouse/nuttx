# `common/src` Component (`boards/risc-v/esp32c6/common/src`)

## Overview
Board-level C implementation (`src`) for `common` (`risc-v/esp32c6`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 18 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[esp_board_adc.c:board_adc_init]` Public function `board_adc_init()`
- `[esp_board_bmp180.c:board_bmp180_initialize]` Public function `board_bmp180_initialize()`
- `[esp_board_i2c.c:board_i2c_init]` Public function `board_i2c_init()`
- `[esp_board_i2s.c:board_i2sdev_initialize]` Public function `board_i2sdev_initialize()`
- `[esp_board_i2s.c:board_i2s_init]` Public function `board_i2s_init()`
- `[esp_board_ledc.c:board_ledc_setup]` Public function `board_ledc_setup()`
- `[esp_board_mcpwm.c:board_motor_initialize]` Public function `board_motor_initialize()`
- `[esp_board_mcpwm.c:board_capture_initialize]` Public function `board_capture_initialize()`
- `[esp_board_mfrc522.c:board_mfrc522_initialize]` Public function `board_mfrc522_initialize()`
- `[esp_board_mmcsd.c:esp_mmcsd_spi_initialize]` Public function `esp_mmcsd_spi_initialize()`
- `[esp_board_mpu60x0.c:board_mpu60x0_initialize]` Public function `board_mpu60x0_initialize()`
- `[esp_board_oa_tc6.c:board_oa_tc6_initialize]` Public function `board_oa_tc6_initialize()`
- `[esp_board_pcnt.c:board_pcnt_initialize]` Public function `board_pcnt_initialize()`
- `[esp_board_rmt.c:board_rmt_rxinitialize]` Public function `board_rmt_rxinitialize()`
- `[esp_board_rmt.c:board_rmt_txinitialize]` Public function `board_rmt_txinitialize()`
- `[esp_board_spi.c:esp_spi2_status]` Public function `esp_spi2_status()`
- `[esp_board_spi.c:esp_spi2_cmddata]` Public function `esp_spi2_cmddata()`
- `[esp_board_spidev.c:board_spidev_initialize]` Public function `board_spidev_initialize()`
- `[esp_board_spiflash.c:board_spiflash_init]` Public function `board_spiflash_init()`
- `[esp_board_spislavedev.c:board_spislavedev_initialize]` Public function `board_spislavedev_initialize()`
- `[esp_board_twai.c:board_twai_setup]` Public function `board_twai_setup()`
- `[esp_board_wlan.c:board_wlan_init]` Public function `board_wlan_init()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BOARD_COMMON`, `CONFIG_CL_MFRC522`, `CONFIG_ESPRESSIF_ADC`, `CONFIG_ESPRESSIF_I2S`, `CONFIG_ESPRESSIF_LEDC` (+16 more)
- `[esp_board_adc.c:board_adc_init]` Validates preconditions and returns `-ENODEV`, `-ENOMEM` on failure
- `[esp_board_bmp180.c:board_bmp180_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[esp_board_i2c.c:board_i2c_init]` Validates preconditions and returns `-ENODEV` on failure
- `[esp_board_i2s.c:board_i2sdev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[esp_board_ledc.c:board_ledc_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[esp_board_mcpwm.c:board_motor_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[esp_board_mfrc522.c:board_mfrc522_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[esp_board_mmcsd.c:esp_mmcsd_spi_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[esp_board_mpu60x0.c:board_mpu60x0_initialize]` Validates preconditions and returns `-ENODEV`, `-ENOMEM` on failure
- `[esp_board_oa_tc6.c:board_oa_tc6_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[esp_board_rmt.c:board_rmt_rxinitialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[esp_board_adc.c:board_adc_init]` Initializes/registers kernel devices or filesystems (`adc_register()`, `esp_adc_initialize()`)
- `[esp_board_bmp180.c:board_bmp180_initialize]` Initializes/registers kernel devices or filesystems (`bmp180_register()`, `esp_i2cbus_bitbang_initialize()`, `esp_i2cbus_initialize()`)
- `[esp_board_i2c.c:board_i2c_init]` Initializes/registers kernel devices or filesystems (`esp_i2cbus_bitbang_initialize()`, `esp_i2cbus_initialize()`, `esp_i2cbus_slave_initialize()`, `i2c_register()`, `i2c_slave_register()`)
- `[esp_board_i2s.c:board_i2sdev_initialize]` Initializes/registers kernel devices or filesystems (`audio_i2s_initialize()`, `audio_register()`, `esp_i2sbus_initialize()`, `i2schar_register()`, `pcm_decode_initialize()`)
- `[esp_board_ledc.c:board_ledc_setup]` Initializes/registers kernel devices or filesystems (`pwm_register()`)
- `[esp_board_mcpwm.c:board_motor_initialize]` Initializes/registers kernel devices or filesystems (`cap_register()`, `esp_mcpwm_capture_initialize()`, `esp_motor_bdc_initialize()`, `motor_register()`)
- `[esp_board_mfrc522.c:board_mfrc522_initialize]` Initializes/registers kernel devices or filesystems (`esp_spibus_initialize()`, `mfrc522_register()`)
- `[esp_board_mmcsd.c:esp_mmcsd_spi_initialize]` Initializes/registers kernel devices or filesystems (`esp_spibus_initialize()`)
- `[esp_board_mpu60x0.c:board_mpu60x0_initialize]` Initializes/registers kernel devices or filesystems (`esp_i2cbus_bitbang_initialize()`, `esp_i2cbus_initialize()`, `mpu60x0_register()`)
- `[esp_board_oa_tc6.c:board_oa_tc6_initialize]` Configures or drives hardware GPIO pins
- `[esp_board_oa_tc6.c:board_oa_tc6_initialize]` Initializes/registers kernel devices or filesystems (`esp_spibus_initialize()`, `oa_tc6_initialize()`)
- `[esp_board_pcnt.c:board_pcnt_initialize]` Initializes/registers kernel devices or filesystems (`cap_register()`)

## Verification
- Run: `./tools/configure.sh sim:nsh && make`
