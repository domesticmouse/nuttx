# `common/include` Component (`boards/xtensa/esp32s2/common/include`)

## Overview
Board-level public headers (`include`) for `common` (`xtensa/esp32s2`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 10 header file(s).

## Interface
- `[esp32s2_board_adc.h:board_adc_init]` Public declaration `board_adc_init()`
- `[esp32s2_board_pcnt.h:board_pcnt_initialize]` Public declaration `board_pcnt_initialize()`
- `[esp32s2_board_rmt.h:board_rmt_rxinitialize]` Public declaration `board_rmt_rxinitialize()`
- `[esp32s2_board_rmt.h:board_rmt_txinitialize]` Public declaration `board_rmt_txinitialize()`
- `[esp32s2_board_sdmmc.h:board_sdmmc_initialize]` Public declaration `board_sdmmc_initialize()`
- `[esp32s2_board_spidev.h:board_spidev_initialize]` Public declaration `board_spidev_initialize()`
- `[esp32s2_board_spislavedev.h:board_spislavedev_initialize]` Public declaration `board_spislavedev_initialize()`
- `[esp32s2_board_wdt.h:board_wdt_init]` Public declaration `board_wdt_init()`
- `[esp32s2_board_wlan.h:board_wlan_init]` Public declaration `board_wlan_init()`
- `[esp32s2_es8311.h:esp32s2_es8311_initialize]` Public declaration `esp32s2_es8311_initialize()`
- `[esp32s2_max6675.h:board_max6675_initialize]` Public declaration `board_max6675_initialize()`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh sim:nsh && make`
