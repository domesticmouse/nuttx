# `common/include` Component (`boards/xtensa/esp32/common/include`)

## Overview
Board-level public headers (`include`) for `common` (`xtensa/esp32`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 30 header file(s).

## Interface
- `[board_qencoder.h:board_qencoder_initialize]` Public declaration `board_qencoder_initialize()`
- `[esp32_backlight.h:esp32_set_backlight]` Public declaration `esp32_set_backlight()`
- `[esp32_bme680.h:board_bme680_initialize]` Public declaration `board_bme680_initialize()`
- `[esp32_bmp180.h:board_bmp180_initialize]` Public declaration `board_bmp180_initialize()`
- `[esp32_bmp280.h:board_bmp280_initialize]` Public declaration `board_bmp280_initialize()`
- `[esp32_board_adc.h:board_adc_init]` Public declaration `board_adc_init()`
- `[esp32_board_apds9960.h:board_apds9960_initialize]` Public declaration `board_apds9960_initialize()`
- `[esp32_board_dac.h:board_dac_initialize]` Public declaration `board_dac_initialize()`
- `[esp32_board_i2c.h:esp32_i2c_register]` Public declaration `esp32_i2c_register()`
- `[esp32_board_mcpwm.h:board_motor_initialize]` Public declaration `board_motor_initialize()`
- `[esp32_board_mcpwm.h:board_capture_initialize]` Public declaration `board_capture_initialize()`
- `[esp32_board_oneshot.h:esp32_oneshot_init]` Public declaration `esp32_oneshot_init()`
- `[esp32_board_pcnt.h:board_pcnt_initialize]` Public declaration `board_pcnt_initialize()`
- `[esp32_board_rmt.h:board_rmt_rxinitialize]` Public declaration `board_rmt_rxinitialize()`
- `[esp32_board_rmt.h:board_rmt_txinitialize]` Public declaration `board_rmt_txinitialize()`
- `[esp32_board_sdmmc.h:board_sdmmc_initialize]` Public declaration `board_sdmmc_initialize()`
- `[esp32_board_spiflash.h:board_spiflash_init]` Public declaration `board_spiflash_init()`
- `[esp32_board_spislavedev.h:board_spislavedev_initialize]` Public declaration `board_spislavedev_initialize()`
- `[esp32_board_wdt.h:board_wdt_init]` Public declaration `board_wdt_init()`
- `[esp32_board_wlan.h:board_wlan_init]` Public declaration `board_wlan_init()`
- `[esp32_es8388.h:esp32_es8388_initialize]` Public declaration `esp32_es8388_initialize()`
- `[esp32_ht16k33.h:board_ht16k33_initialize]` Public declaration `board_ht16k33_initialize()`
- `[esp32_lcd_backpack.h:board_lcd_backpack_init]` Public declaration `board_lcd_backpack_init()`
- `[esp32_ltr308.h:board_ltr308_initialize]` Public declaration `board_ltr308_initialize()`
- `[esp32_max6675.h:board_max6675_initialize]` Public declaration `board_max6675_initialize()`
- *(+9 additional symbols across 30 files)*

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh sim:nsh && make`
