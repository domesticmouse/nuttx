# `common/include` Component (`boards/risc-v/esp32c2/common/include`)

## Overview
Board-level public headers (`include`) for `common` (`risc-v/esp32c2`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 11 header file(s).

## Interface
- `[esp_board_adc.h:board_adc_init]` Public declaration `board_adc_init()`
- `[esp_board_bmp180.h:board_bmp180_initialize]` Public declaration `board_bmp180_initialize()`
- `[esp_board_bmp280.h:board_bmp280_initialize]` Public declaration `board_bmp280_initialize()`
- `[esp_board_i2c.h:board_i2c_init]` Public declaration `board_i2c_init()`
- `[esp_board_ledc.h:board_ledc_setup]` Public declaration `board_ledc_setup()`
- `[esp_board_mmcsd.h:esp_mmcsd_spi_initialize]` Public declaration `esp_mmcsd_spi_initialize()`
- `[esp_board_rng90.h:board_rng90_initialize]` Public declaration `board_rng90_initialize()`
- `[esp_board_spidev.h:board_spidev_initialize]` Public declaration `board_spidev_initialize()`
- `[esp_board_spiflash.h:board_spiflash_init]` Public declaration `board_spiflash_init()`
- `[esp_board_spislavedev.h:board_spislavedev_initialize]` Public declaration `board_spislavedev_initialize()`
- `[esp_board_wlan.h:board_wlan_init]` Public declaration `board_wlan_init()`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh sim:nsh && make`
