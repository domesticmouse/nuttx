# `lx_cpu/include` Component (`boards/arm/lpc17xx_40xx/lx_cpu/include`)

## Overview
Board-level public headers (`include`) for `lx_cpu` (`arm/lpc17xx_40xx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:nuttx_ulan_get_chip_data]` Public declaration `nuttx_ulan_get_chip_data()`
- `[board.h:nuttx_ulan_chip_data_s]` Type definition `nuttx_ulan_chip_data_s`
- `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `BOARD_OSCCLK_FREQUENCY`, `BOARD_RTCCLK_FREQUENCY`, `BOARD_INTRCOSC_FREQUENCY`, `BOARD_WDTOSC_FREQUENCY`, `LPC17_40_CCLK` (+123 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh lx_cpu:nsh && make`
