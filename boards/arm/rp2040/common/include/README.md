# `common/include` Component (`boards/arm/rp2040/common/include`)

## Overview
Board-level public headers (`include`) for `common` (`arm/rp2040`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 12 header file(s).

## Interface
- `[rp2040_ads7046.h:board_ads7046_initialize]` Public declaration `board_ads7046_initialize()`
- `[rp2040_bmp180.h:board_bmp180_initialize]` Public declaration `board_bmp180_initialize()`
- `[rp2040_bmp280.h:board_bmp280_initialize]` Public declaration `board_bmp280_initialize()`
- `[rp2040_common_bringup.h:rp2040_common_bringup]` Public declaration `rp2040_common_bringup()`
- `[rp2040_common_initialize.h:rp2040_common_earlyinitialize]` Public declaration `rp2040_common_earlyinitialize()`
- `[rp2040_common_initialize.h:rp2040_common_initialize]` Public declaration `rp2040_common_initialize()`
- `[rp2040_common_pico.h:rp2040_dev_gpio_init]` Public declaration `rp2040_dev_gpio_init()`
- `[rp2040_ina219.h:board_ina219_initialize]` Public declaration `board_ina219_initialize()`
- `[rp2040_lcd_backpack.h:board_lcd_backpack_init]` Public declaration `board_lcd_backpack_init()`
- `[rp2040_max6675.h:board_max6675_initialize]` Public declaration `board_max6675_initialize()`
- `[rp2040_pwmdev.h:rp2040_pwmdev_initialize]` Public declaration `rp2040_pwmdev_initialize()`
- `[rp2040_tmp112.h:board_tmp112_initialize]` Public declaration `board_tmp112_initialize()`
- `[rp2040_uniqueid.h:rp2040_uniqueid_initialize]` Public declaration `rp2040_uniqueid_initialize()`
- `[rp2040_uniqueid.h:RP2040_FLASH_ID_SIZE]` Hardware/board configuration macros (`RP2040_FLASH_ID_SIZE`, `RP2040_FLASH_ID_BUFFER_SIZE`, `RP2040_FLASH_ID_BUFFER_OFFSET`, `RP2040_FLASH_RUID_CMD`)

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh sim:nsh && make`
