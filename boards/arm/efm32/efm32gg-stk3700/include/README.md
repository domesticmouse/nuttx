# `efm32gg-stk3700/include` Component (`boards/arm/efm32/efm32gg-stk3700/include`)

## Overview
Board-level public headers (`include`) for `efm32gg-stk3700` (`arm/efm32`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:board_format_sdcard]` Public declaration `board_format_sdcard()`
- `[board.h:board_mount_sdcard]` Public declaration `board_mount_sdcard()`
- `[board.h:board_umount_sdcard]` Public declaration `board_umount_sdcard()`
- `[board.h:board_is_usb_connected]` Public declaration `board_is_usb_connected()`
- `[board.h:board_is_usb_enabled]` Public declaration `board_is_usb_enabled()`
- `[board.h:board_enable_usbmsc]` Public declaration `board_enable_usbmsc()`
- `[board.h:board_disable_usbmsc]` Public declaration `board_disable_usbmsc()`
- `[board.h:efm32_ledinit]` Public declaration `efm32_ledinit()`
- `[board.h:efm32_setled]` Public declaration `efm32_setled()`
- `[board.h:efm32_setleds]` Public declaration `efm32_setleds()`
- `[board.h:BOARD_HAVE_HFXO]` Hardware/board configuration macros (`BOARD_HAVE_HFXO`, `BOARD_HAVE_LFXO`, `BOARD_HFRCO_FREQUENCY`, `BOARD_HFXO_FREQUENCY`, `BOARD_LFRCO_FREQUENCY`, `BOARD_LFXO_FREQUENCY` (+76 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh efm32gg-stk3700:nsh && make`
