# `xiao-rp2350/include` Component (`boards/arm/rp23xx/xiao-rp2350/include`)

## Overview
Board-level public headers (`include`) for `xiao-rp2350` (`arm/rp23xx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 5 header file(s).

## Interface
- `[board.h:rp23xx_boardearlyinitialize]` Public declaration `rp23xx_boardearlyinitialize()`
- `[board.h:rp23xx_boardinitialize]` Public declaration `rp23xx_boardinitialize()`
- `[board.h:MHZ]` Hardware/board configuration macros (`MHZ`, `BOARD_XOSC_FREQ`, `BOARD_XOSC_STARTUPDELAY`, `BOARD_PLL_SYS_FREQ`, `BOARD_PLL_USB_FREQ`, `BOARD_REF_FREQ` (+26 more))
- `[rp23xx_i2cdev.h:board_i2cdev_initialize]` Public declaration `board_i2cdev_initialize()`
- `[rp23xx_i2sdev.h:board_i2sdev_initialize]` Public declaration `board_i2sdev_initialize()`
- `[rp23xx_spidev.h:board_spidev_initialize]` Public declaration `board_spidev_initialize()`
- `[rp23xx_spisd.h:board_spisd_initialize]` Public declaration `board_spisd_initialize()`
- `[rp23xx_spisd.h:board_spisd_status]` Public declaration `board_spisd_status()`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh xiao-rp2350:nsh && make`
