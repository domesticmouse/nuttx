# `esp32-2432S028/src` Component (`boards/xtensa/esp32/esp32-2432S028/src`)

## Overview
Board-level C implementation (`src`) for `esp32-2432S028` (`xtensa/esp32`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[esp32-2432S028.h:esp32_bringup]` Public declaration `esp32_bringup()`
- `[esp32-2432S028.h:esp32_spiflash_init]` Public declaration `esp32_spiflash_init()`
- `[esp32-2432S028.h:BUTTON_BOOT]` Hardware/board configuration macros (`BUTTON_BOOT`, `GPIO_LED_RED`, `GPIO_LED_GREEN`, `GPIO_LED_BLUE`, `PCNT_QE0_ID`, `TIMER0` (+5 more))
- `[esp32_boot.c:esp32_board_initialize]` Public function `esp32_board_initialize()`
- `[esp32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[esp32_bringup.c:esp32_bringup]` Public function `esp32_bringup()`
- `[esp32_reset.c:board_reset]` Public function `board_reset()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_BOARDCTL_RESET`

## Side Effects
- `[esp32_bringup.c:esp32_bringup]` Initializes/registers kernel devices or filesystems (`board_lcd_initialize()`, `board_pcnt_initialize()`, `board_qencoder_initialize()`, `btn_lower_initialize()`, `esp32_ble_initialize()`)

## Verification
- Run: `./tools/configure.sh esp32-2432S028:nsh && make`
