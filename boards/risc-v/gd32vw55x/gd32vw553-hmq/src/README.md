# `gd32vw553-hmq/src` Component (`boards/risc-v/gd32vw55x/gd32vw553-hmq/src`)

## Overview
Board-level C implementation (`src`) for `gd32vw553-hmq` (`risc-v/gd32vw55x`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[gd32vw553-hmq.h:gd32_bringup]` Public declaration `gd32_bringup()`
- `[gd32vw553-hmq.h:gd32_spidev_initialize]` Public declaration `gd32_spidev_initialize()`
- `[gd32_appinit.c:board_app_initialize]` Public function `board_app_initialize()`
- `[gd32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[gd32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[gd32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[gd32_boot.c:gd32vw55x_boardinitialize]` Public function `gd32vw55x_boardinitialize()`
- `[gd32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[gd32_bringup.c:gdwifi_start]` Public function `gdwifi_start()`
- `[gd32_bringup.c:gd32_ble_initialize]` Public function `gd32_ble_initialize()`
- `[gd32_bringup.c:gd32_bringup]` Public function `gd32_bringup()`
- `[gd32_reset.c:board_reset]` Public function `board_reset()`
- `[gd32_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[gd32_userleds.c:board_userled]` Public function `board_userled()`
- `[gd32_userleds.c:board_userled_all]` Public function `board_userled_all()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_LEDS`, `CONFIG_BOARDCTL`, `CONFIG_BOARDCTL_RESET`, `CONFIG_USERLED`

## Side Effects
- `[gd32_bringup.c:gdwifi_start]` Initializes/registers kernel devices or filesystems (`adc_register()`, `cap_register()`, `gd32_adc_initialize()`, `gd32_cap_initialize()`, `gd32_fwdgt_initialize()`)
- `[gd32_reset.c:board_reset]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)

## Verification
- Run: `./tools/configure.sh gd32vw553-hmq:nsh && make`
