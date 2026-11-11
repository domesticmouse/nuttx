# `common/include` Component (`boards/risc-v/esp32c3-legacy/common/include`)

## Overview
Board-level public headers (`include`) for `common` (`risc-v/esp32c3-legacy`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 14 header file(s).

## Interface
- `[esp32c3_board_adc.h:board_adc_init]` Public declaration `board_adc_init()`
- `[esp32c3_board_apds9960.h:board_apds9960_initialize]` Public declaration `board_apds9960_initialize()`
- `[esp32c3_board_bmp180.h:board_bmp180_initialize]` Public declaration `board_bmp180_initialize()`
- `[esp32c3_board_i2c.h:board_i2c_init]` Public declaration `board_i2c_init()`
- `[esp32c3_board_ice40.h:esp32c3_ice40_setup]` Public declaration `esp32c3_ice40_setup()`
- `[esp32c3_board_ledc.h:board_ledc_setup]` Public declaration `board_ledc_setup()`
- `[esp32c3_board_mpu60x0_i2c.h:board_mpu60x0_initialize]` Public declaration `board_mpu60x0_initialize()`
- `[esp32c3_board_oneshot.h:board_oneshot_init]` Public declaration `board_oneshot_init()`
- `[esp32c3_board_spidev.h:board_spidev_initialize]` Public declaration `board_spidev_initialize()`
- `[esp32c3_board_spiflash.h:board_spiflash_init]` Public declaration `board_spiflash_init()`
- `[esp32c3_board_spislavedev.h:board_spislavedev_initialize]` Public declaration `board_spislavedev_initialize()`
- `[esp32c3_board_twai.h:board_twai_setup]` Public declaration `board_twai_setup()`
- `[esp32c3_board_wdt.h:board_wdt_init]` Public declaration `board_wdt_init()`
- `[esp32c3_board_wlan.h:board_wlan_init]` Public declaration `board_wlan_init()`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh sim:nsh && make`
