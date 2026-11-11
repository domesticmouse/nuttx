# `avaota-a1/src` Component (`boards/arm64/a527/avaota-a1/src`)

## Overview
Board-level C implementation (`src`) for `avaota-a1` (`arm64/a527`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[avaota-a1.h:a527_bringup]` Public declaration `a527_bringup()`
- `[a527_boardinit.c:a527_memory_initialize]` Public function `a527_memory_initialize()`
- `[a527_boardinit.c:a527_board_initialize]` Public function `a527_board_initialize()`
- `[a527_boardinit.c:board_late_initialize]` Public function `board_late_initialize()`
- `[a527_bringup.c:a527_bringup]` Public function `a527_bringup()`
- `[a527_power.c:board_power_off]` Public function `board_power_off()`
- `[a527_power.c:board_reset]` Public function `board_reset()`

## Invariants
- None

## Side Effects
- `[a527_bringup.c:a527_bringup]` Initializes/registers kernel devices or filesystems (`nx_mount()`)

## Verification
- Run: `./tools/configure.sh avaota-a1:nsh && make`
