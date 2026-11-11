# `esp32s3-meadow/src` Component (`boards/xtensa/esp32s3/esp32s3-meadow/src`)

## Overview
Board-level C implementation (`src`) for `esp32s3-meadow` (`xtensa/esp32s3`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[esp32s3-meadow.h:esp32s3_bringup]` Public declaration `esp32s3_bringup()`
- `[esp32s3_boot.c:esp32s3_board_initialize]` Public function `esp32s3_board_initialize()`
- `[esp32s3_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[esp32s3_bringup.c:esp32s3_bringup]` Public function `esp32s3_bringup()`
- `[esp32s3_reset.c:board_reset]` Public function `board_reset()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_BOARDCTL_RESET`

## Side Effects
- `[esp32s3_bringup.c:esp32s3_bringup]` Initializes/registers kernel devices or filesystems (`btn_lower_initialize()`, `nx_mount()`)

## Verification
- Run: `./tools/configure.sh esp32s3-meadow:nsh && make`
