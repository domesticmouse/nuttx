# `pinephonepro/src` Component (`boards/arm64/rk3399/pinephonepro/src`)

## Overview
Board-level C implementation (`src`) for `pinephonepro` (`arm64/rk3399`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[pinephonepro.h:pinephonepro_bringup]` Public declaration `pinephonepro_bringup()`
- `[pinephonepro_boardinit.c:rk3399_memory_initialize]` Public function `rk3399_memory_initialize()`
- `[pinephonepro_boardinit.c:rk3399_board_initialize]` Public function `rk3399_board_initialize()`
- `[pinephonepro_boardinit.c:board_late_initialize]` Public function `board_late_initialize()`
- `[pinephonepro_bringup.c:pinephonepro_bringup]` Public function `pinephonepro_bringup()`
- `[pinephonepro_reset.c:board_reset]` Public function `board_reset()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_BOARDCTL_RESET`

## Side Effects
- `[pinephonepro_bringup.c:pinephonepro_bringup]` Initializes/registers kernel devices or filesystems (`nx_mount()`)

## Verification
- Run: `./tools/configure.sh pinephonepro:nsh && make`
