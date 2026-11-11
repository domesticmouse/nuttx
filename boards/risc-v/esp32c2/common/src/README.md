# `common/src` Component (`boards/risc-v/esp32c2/common/src`)

## Overview
Board-level C implementation (`src`) for `common` (`risc-v/esp32c2`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 12 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[esp_board_adc.c:board_adc_init]` Public function `board_adc_init()`
- `[esp_board_bmp180.c:board_bmp180_initialize]` Public function `board_bmp180_initialize()`
- `[esp_board_bmp280.c:board_bmp280_initialize]` Public function `board_bmp280_initialize()`
- `[esp_board_i2c.c:board_i2c_init]` Public function `board_i2c_init()`
- `[esp_board_ledc.c:board_ledc_setup]` Public function `board_ledc_setup()`
- `[esp_board_mmcsd.c:esp_mmcsd_spi_initialize]` Public function `esp_mmcsd_spi_initialize()`
- `[esp_board_rng90.c:board_rng90_initialize]` Public function `board_rng90_initialize()`
- `[esp_board_spi.c:esp_spi2_status]` Public function `esp_spi2_status()`
- `[esp_board_spi.c:esp_spi2_cmddata]` Public function `esp_spi2_cmddata()`
- `[esp_board_spidev.c:board_spidev_initialize]` Public function `board_spidev_initialize()`
- `[esp_board_spiflash.c:board_spiflash_init]` Public function `board_spiflash_init()`
- `[esp_board_spislavedev.c:board_spislavedev_initialize]` Public function `board_spislavedev_initialize()`
- `[esp_board_wlan.c:board_wlan_init]` Public function `board_wlan_init()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BOARD_COMMON`, `CONFIG_DEV_RNG90`, `CONFIG_ESPRESSIF_ADC`, `CONFIG_ESPRESSIF_LEDC`, `CONFIG_ESPRESSIF_SPI` (+9 more)
- `[esp_board_adc.c:board_adc_init]` Validates preconditions and returns `-ENODEV`, `-ENOMEM` on failure
- `[esp_board_bmp180.c:board_bmp180_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[esp_board_bmp280.c:board_bmp280_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[esp_board_i2c.c:board_i2c_init]` Validates preconditions and returns `-ENODEV` on failure
- `[esp_board_ledc.c:board_ledc_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[esp_board_mmcsd.c:esp_mmcsd_spi_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[esp_board_rng90.c:board_rng90_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[esp_board_spi.c:esp_spi2_status]` Validates preconditions and returns `-ENODEV` on failure
- `[esp_board_spidev.c:board_spidev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[esp_board_spiflash.c:board_spiflash_init]` Validates preconditions and returns `-ENODEV` on failure
- `[esp_board_spislavedev.c:board_spislavedev_initialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[esp_board_adc.c:board_adc_init]` Initializes/registers kernel devices or filesystems (`adc_register()`, `esp_adc_initialize()`)
- `[esp_board_bmp180.c:board_bmp180_initialize]` Initializes/registers kernel devices or filesystems (`bmp180_register()`, `esp_i2cbus_bitbang_initialize()`, `esp_i2cbus_initialize()`)
- `[esp_board_bmp280.c:board_bmp280_initialize]` Initializes/registers kernel devices or filesystems (`bmp280_register()`, `esp_i2cbus_bitbang_initialize()`, `esp_i2cbus_initialize()`)
- `[esp_board_i2c.c:board_i2c_init]` Initializes/registers kernel devices or filesystems (`esp_i2cbus_bitbang_initialize()`, `esp_i2cbus_initialize()`, `esp_i2cbus_slave_initialize()`, `i2c_register()`, `i2c_slave_register()`)
- `[esp_board_ledc.c:board_ledc_setup]` Initializes/registers kernel devices or filesystems (`pwm_register()`)
- `[esp_board_mmcsd.c:esp_mmcsd_spi_initialize]` Initializes/registers kernel devices or filesystems (`esp_spibus_initialize()`)
- `[esp_board_rng90.c:board_rng90_initialize]` Initializes/registers kernel devices or filesystems (`esp_i2cbus_bitbang_initialize()`, `esp_i2cbus_initialize()`, `rng90_register()`)
- `[esp_board_spi.c:esp_spi2_status]` Configures or drives hardware GPIO pins
- `[esp_board_spidev.c:board_spidev_initialize]` Initializes/registers kernel devices or filesystems (`esp_spibus_initialize()`, `spi_register()`)
- `[esp_board_spiflash.c:board_spiflash_init]` Initializes/registers kernel devices or filesystems (`mtdconfig_register()`, `nx_mount()`, `nxffs_initialize()`, `smart_initialize()`)
- `[esp_board_spislavedev.c:board_spislavedev_initialize]` Initializes/registers kernel devices or filesystems (`esp_spislave_ctrlr_initialize()`, `spi_slave_register()`)
- `[esp_board_wlan.c:board_wlan_init]` Initializes/registers kernel devices or filesystems (`esp_wlan_softap_initialize()`, `esp_wlan_sta_initialize()`)

## Verification
- Run: `./tools/configure.sh sim:nsh && make`
