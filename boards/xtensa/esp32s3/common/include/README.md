# `common/include` Component (`boards/xtensa/esp32s3/common/include`)

## Overview
Board-level public headers (`include`) for `common` (`xtensa/esp32s3`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 11 header file(s).

## Interface
- `[esp32s3_board_adc.h:board_adc_init]` Public declaration `board_adc_init()`
- `[esp32s3_board_ledc.h:esp32s3_pwm_setup]` Public declaration `esp32s3_pwm_setup()`
- `[esp32s3_board_mcpwm.h:board_motor_initialize]` Public declaration `board_motor_initialize()`
- `[esp32s3_board_mcpwm.h:board_capture_initialize]` Public declaration `board_capture_initialize()`
- `[esp32s3_board_pcnt.h:board_pcnt_initialize]` Public declaration `board_pcnt_initialize()`
- `[esp32s3_board_rmt.h:board_rmt_rxinitialize]` Public declaration `board_rmt_rxinitialize()`
- `[esp32s3_board_rmt.h:board_rmt_txinitialize]` Public declaration `board_rmt_txinitialize()`
- `[esp32s3_board_sdmmc.h:board_sdmmc_initialize]` Public declaration `board_sdmmc_initialize()`
- `[esp32s3_board_sdmmc.h:board_sdmmc_spi_initialize]` Public declaration `board_sdmmc_spi_initialize()`
- `[esp32s3_board_spidev.h:board_spidev_initialize]` Public declaration `board_spidev_initialize()`
- `[esp32s3_board_spislavedev.h:board_spislavedev_initialize]` Public declaration `board_spislavedev_initialize()`
- `[esp32s3_board_tim.h:board_tim_init]` Public declaration `board_tim_init()`
- `[esp32s3_board_wdt.h:board_wdt_init]` Public declaration `board_wdt_init()`
- `[esp32s3_board_wlan.h:board_wlan_init]` Public declaration `board_wlan_init()`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh sim:nsh && make`
