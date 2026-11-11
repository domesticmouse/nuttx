# `common/src` Component (`boards/xtensa/esp32s2/common/src`)

## Overview
Board-level C implementation (`src`) for `common` (`xtensa/esp32s2`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 17 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[esp32s2_board_adc.c:board_adc_init]` Public function `board_adc_init()`
- `[esp32s2_board_i2sdev.c:board_i2sdev_initialize]` Public function `board_i2sdev_initialize()`
- `[esp32s2_board_pcnt.c:board_pcnt_initialize]` Public function `board_pcnt_initialize()`
- `[esp32s2_board_rmt.c:board_rmt_rxinitialize]` Public function `board_rmt_rxinitialize()`
- `[esp32s2_board_rmt.c:board_rmt_txinitialize]` Public function `board_rmt_txinitialize()`
- `[esp32s2_board_sdmmc.c:board_sdmmc_initialize]` Public function `board_sdmmc_initialize()`
- `[esp32s2_board_spi.c:esp32s2_spi2_status]` Public function `esp32s2_spi2_status()`
- `[esp32s2_board_spi.c:esp32s2_spi2_cmddata]` Public function `esp32s2_spi2_cmddata()`
- `[esp32s2_board_spi.c:esp32s2_spi3_status]` Public function `esp32s2_spi3_status()`
- `[esp32s2_board_spi.c:esp32s2_spi3_cmddata]` Public function `esp32s2_spi3_cmddata()`
- `[esp32s2_board_spidev.c:board_spidev_initialize]` Public function `board_spidev_initialize()`
- `[esp32s2_board_spiflash.c:board_spiflash_init]` Public function `board_spiflash_init()`
- `[esp32s2_board_spislavedev.c:board_spislavedev_initialize]` Public function `board_spislavedev_initialize()`
- `[esp32s2_board_twai.c:board_twai_setup]` Public function `board_twai_setup()`
- `[esp32s2_board_wdt.c:board_wdt_init]` Public function `board_wdt_init()`
- `[esp32s2_board_wlan.c:board_wlan_init]` Public function `board_wlan_init()`
- `[esp32s2_cs4344.c:esp32s2_cs4344_initialize]` Public function `esp32s2_cs4344_initialize()`
- `[esp32s2_es8311.c:esp32s2_es8311_initialize]` Public function `esp32s2_es8311_initialize()`
- `[esp32s2_ili9341.c:board_lcd_initialize]` Public function `board_lcd_initialize()`
- `[esp32s2_ili9341.c:board_lcd_getdev]` Public function `board_lcd_getdev()`
- `[esp32s2_ili9341.c:board_lcd_uninitialize]` Public function `board_lcd_uninitialize()`
- `[esp32s2_max6675.c:board_max6675_initialize]` Public function `board_max6675_initialize()`
- `[esp32s2_st7789.c:board_lcd_initialize]` Public function `board_lcd_initialize()`
- *(+2 additional symbols across 17 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BOARD_COMMON`, `CONFIG_ARCH_BUTTONS`, `CONFIG_AUDIO_CS4344`, `CONFIG_AUDIO_ES8311`, `CONFIG_DEV_GPIO` (+18 more)
- `[esp32s2_board_adc.c:board_adc_init]` Validates preconditions and returns `-ENODEV`, `-ENOMEM` on failure
- `[esp32s2_board_i2sdev.c:board_i2sdev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32s2_board_rmt.c:board_rmt_rxinitialize]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32s2_board_sdmmc.c:board_sdmmc_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32s2_board_spi.c:esp32s2_spi2_status]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32s2_board_spidev.c:board_spidev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32s2_board_spiflash.c:board_spiflash_init]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32s2_board_spislavedev.c:board_spislavedev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32s2_board_twai.c:board_twai_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32s2_cs4344.c:esp32s2_cs4344_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32s2_es8311.c:esp32s2_es8311_initialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[esp32s2_board_adc.c:board_adc_init]` Initializes/registers kernel devices or filesystems (`adc_register()`, `board_adc_register()`, `esp_adc_initialize()`)
- `[esp32s2_board_i2sdev.c:board_i2sdev_initialize]` Initializes/registers kernel devices or filesystems (`audio_i2s_initialize()`, `audio_register()`, `esp_i2sbus_initialize()`, `i2schar_register()`, `pcm_decode_initialize()`)
- `[esp32s2_board_pcnt.c:board_pcnt_initialize]` Initializes/registers kernel devices or filesystems (`cap_register()`)
- `[esp32s2_board_rmt.c:board_rmt_rxinitialize]` Initializes/registers kernel devices or filesystems (`esp_lirc_rx_initialize()`, `esp_lirc_tx_initialize()`)
- `[esp32s2_board_sdmmc.c:board_sdmmc_initialize]` Initializes/registers kernel devices or filesystems (`esp32s2_spibus_initialize()`)
- `[esp32s2_board_spi.c:esp32s2_spi2_status]` Configures or drives hardware GPIO pins
- `[esp32s2_board_spidev.c:board_spidev_initialize]` Initializes/registers kernel devices or filesystems (`esp32s2_spibus_initialize()`, `spi_register()`)
- `[esp32s2_board_spiflash.c:board_spiflash_init]` Initializes/registers kernel devices or filesystems (`nx_mount()`, `nxffs_initialize()`, `smart_initialize()`)
- `[esp32s2_board_spislavedev.c:board_spislavedev_initialize]` Initializes/registers kernel devices or filesystems (`esp32s2_spislave_ctrlr_initialize()`, `spi_slave_register()`)
- `[esp32s2_board_twai.c:board_twai_setup]` Initializes/registers kernel devices or filesystems (`can_register()`)
- `[esp32s2_board_wdt.c:board_wdt_init]` Initializes/registers kernel devices or filesystems (`esp32s2_wdt_initialize()`)
- `[esp32s2_board_wlan.c:board_wlan_init]` Initializes/registers kernel devices or filesystems (`esp_wlan_softap_initialize()`, `esp_wlan_sta_initialize()`)

## Verification
- Run: `./tools/configure.sh sim:nsh && make`
