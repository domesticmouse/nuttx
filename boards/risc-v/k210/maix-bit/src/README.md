# `maix-bit/src` Component (`boards/risc-v/k210/maix-bit/src`)

## Overview
Board-level C implementation (`src`) for `maix-bit` (`risc-v/k210`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[maix-bit.h:k210_bringup]` Public declaration `k210_bringup()`
- `[k210_boot.c:k210_boardinitialize]` Public function `k210_boardinitialize()`
- `[k210_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[k210_bringup.c:k210_bringup]` Public function `k210_bringup()`
- `[k210_leds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[k210_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[k210_leds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[k210_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[k210_userleds.c:board_userled]` Public function `board_userled()`
- `[k210_userleds.c:board_userled_all]` Public function `board_userled_all()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_LEDS`, `CONFIG_USERLED_LOWER`

## Side Effects
- `[k210_boot.c:k210_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[k210_bringup.c:k210_bringup]` Initializes/registers kernel devices or filesystems (`k210_wdt_initialize()`, `nx_mount()`, `userled_lower_initialize()`)

## Verification
- Run: `./tools/configure.sh maix-bit:nsh && make`
