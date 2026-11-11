# `esp32s3-m5-cardputer/include` Component (`boards/xtensa/esp32s3/esp32s3-m5-cardputer/include`)

## Overview
Board-level public headers (`include`) for `esp32s3-m5-cardputer` (`xtensa/esp32s3`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `BOARD_CLOCK_FREQUENCY`, `CARDPUTER_GPIO_USB_DM`, `CARDPUTER_GPIO_USB_DP`, `CARDPUTER_GPIO_KB_A0`, `CARDPUTER_GPIO_KB_A1` (+29 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh esp32s3-m5-cardputer:nsh && make`
