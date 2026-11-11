# `esp32-ethernet-kit/src` Component (`boards/xtensa/esp32/esp32-ethernet-kit/src`)

## Overview
Board-level C implementation (`src`) for `esp32-ethernet-kit` (`xtensa/esp32`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[esp32-ethernet-kit.h:esp32_bringup]` Public declaration `esp32_bringup()`
- `[esp32-ethernet-kit.h:esp32_spiflash_init]` Public declaration `esp32_spiflash_init()`
- `[esp32-ethernet-kit.h:BUTTON_BOOT]` Hardware/board configuration macros (`BUTTON_BOOT`, `TIMER0`, `TIMER1`, `TIMER2`, `TIMER3`, `ONESHOT_TIMER` (+1 more))
- `[esp32_boot.c:esp32_board_initialize]` Public function `esp32_board_initialize()`
- `[esp32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[esp32_bringup.c:esp32_bringup]` Public function `esp32_bringup()`
- `[esp32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[esp32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[esp32_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[esp32_reset.c:board_reset]` Public function `board_reset()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_BOARDCTL_RESET`

## Side Effects
- `[esp32_bringup.c:esp32_bringup]` Initializes/registers kernel devices or filesystems (`board_sdmmc_initialize()`, `btn_lower_initialize()`, `esp32_ble_initialize()`, `esp32_timer_initialize()`, `nx_mount()`)
- `[esp32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh esp32-ethernet-kit:nsh && make`
