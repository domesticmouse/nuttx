# `esp32c3-legacy-devkit-rust-1/src` Component (`boards/risc-v/esp32c3-legacy/esp32c3-legacy-devkit-rust-1/src`)

## Overview
Board-level C implementation (`src`) for `esp32c3-legacy-devkit-rust-1` (`risc-v/esp32c3-legacy`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 6 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[esp32c3-legacy-devkit-rust-1.h:esp32c3_bringup]` Public declaration `esp32c3_bringup()`
- `[esp32c3-legacy-devkit-rust-1.h:TIMER0]` Hardware/board configuration macros (`TIMER0`, `TIMER1`, `ONESHOT_TIMER`, `ONESHOT_RESOLUTION_US`)
- `[esp32c3_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[esp32c3_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[esp32c3_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[esp32c3_boot.c:esp32c3_board_initialize]` Public function `esp32c3_board_initialize()`
- `[esp32c3_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[esp32c3_bringup.c:esp32c3_bringup]` Public function `esp32c3_bringup()`
- `[esp32c3_ioctl.c:board_ioctl]` Public function `board_ioctl()`
- `[esp32c3_reset.c:board_reset]` Public function `board_reset()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_LEDS`, `CONFIG_BOARDCTL_IOCTL`, `CONFIG_BOARDCTL_RESET`
- `[esp32c3_ioctl.c:board_ioctl]` Validates preconditions and returns `-ENOTTY` on failure

## Side Effects
- `[esp32c3_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[esp32c3_boot.c:esp32c3_board_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[esp32c3_bringup.c:esp32c3_bringup]` Initializes/registers kernel devices or filesystems (`board_apds9960_initialize()`, `esp32c3_efuse_initialize()`, `fb_register()`, `nx_mount()`)

## Verification
- Run: `./tools/configure.sh esp32c3-legacy-devkit-rust-1:nsh && make`
