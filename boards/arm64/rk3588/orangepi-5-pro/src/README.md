# `orangepi-5-pro/src` Component (`boards/arm64/rk3588/orangepi-5-pro/src`)

## Overview
Board-level C implementation (`src`) for `orangepi-5-pro` (`arm64/rk3588`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[orangepi5pro.h:orangepi5pro_bringup]` Public declaration `orangepi5pro_bringup()`
- `[orangepi5pro_boardinit.c:rk3588_memory_initialize]` Public function `rk3588_memory_initialize()`
- `[orangepi5pro_boardinit.c:rk3588_board_initialize]` Public function `rk3588_board_initialize()`
- `[orangepi5pro_boardinit.c:board_late_initialize]` Public function `board_late_initialize()`
- `[orangepi5pro_bringup.c:orangepi5pro_bringup]` Public function `orangepi5pro_bringup()`
- `[orangepi5pro_reset.c:board_reset]` Public function `board_reset()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_BOARDCTL_RESET`

## Side Effects
- `[orangepi5pro_bringup.c:orangepi5pro_bringup]` Initializes/registers kernel devices or filesystems (`nx_mount()`)

## Verification
- Run: `./tools/configure.sh orangepi-5-pro:nsh && make`
