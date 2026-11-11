# `rddrone-bms772/include` Component (`boards/arm/s32k1xx/rddrone-bms772/include`)

## Overview
Board-level public headers (`include`) for `rddrone-bms772` (`arm/s32k1xx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s).

## Interface
- `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `RDDRONE_BMS772_RUN_SYSCLK_FREQUENCY`, `RDDRONE_BMS772_VLPR_SYSCLK_FREQUENCY`, `BOARD_LED_R`, `BOARD_LED_G`, `BOARD_LED_B` (+30 more))
- `[smbus_sbd.h:smbus_sbd_initialize]` Public declaration `smbus_sbd_initialize()`
- `[smbus_sbd.h:smbus_sbd_data_s]` Type definition `smbus_sbd_data_s`
- `[smbus_sbd.h:SBD_MANUFACTURER_ACCESS]` Hardware/board configuration macros (`SBD_MANUFACTURER_ACCESS`, `SBD_REMAINING_CAPACITY_ALARM`, `SBD_REMAINING_TIME_ALARM`, `SBD_BATTERY_MODE`, `SBD_AT_RATE`, `SBD_AT_RATE_TIME_TO_FULL` (+33 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh rddrone-bms772:nsh && make`
