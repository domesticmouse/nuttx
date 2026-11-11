# `w5500-evb-pico/include` Component (`boards/arm/rp2040/w5500-evb-pico/include`)

## Overview
Board-level public headers (`include`) for `w5500-evb-pico` (`arm/rp2040`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 5 header file(s).

## Interface
- `[board.h:rp2040_boardearlyinitialize]` Public declaration `rp2040_boardearlyinitialize()`
- `[board.h:rp2040_boardinitialize]` Public declaration `rp2040_boardinitialize()`
- `[board.h:MHZ]` Hardware/board configuration macros (`MHZ`, `BOARD_XOSC_FREQ`, `BOARD_XOSC_STARTUPDELAY`, `BOARD_PLL_SYS_FREQ`, `BOARD_PLL_USB_FREQ`, `BOARD_REF_FREQ` (+28 more))
- `[rp2040_i2cdev.h:board_i2cdev_initialize]` Public declaration `board_i2cdev_initialize()`
- `[rp2040_i2sdev.h:board_i2sdev_initialize]` Public declaration `board_i2sdev_initialize()`
- `[rp2040_spidev.h:board_spidev_initialize]` Public declaration `board_spidev_initialize()`
- `[rp2040_spisd.h:board_spisd_initialize]` Public declaration `board_spisd_initialize()`
- `[rp2040_spisd.h:board_spisd_status]` Public declaration `board_spisd_status()`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh w5500-evb-pico:usbnsh && make`
