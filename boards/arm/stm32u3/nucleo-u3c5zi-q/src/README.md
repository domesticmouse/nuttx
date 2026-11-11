# `nucleo-u3c5zi-q/src` Component (`boards/arm/stm32u3/nucleo-u3c5zi-q/src`)

## Overview
Board-level C implementation (`src`) for `nucleo-u3c5zi-q` (`arm/stm32u3`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 3 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[nucleo-u3c5zi-q.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[stm32_boot.c:stm32_board_initialize]` Public function `stm32_board_initialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`

## Side Effects
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`stm32_common_initialize()`)

## Verification
- Run: `./tools/configure.sh nucleo-u3c5zi-q:nsh && make`
