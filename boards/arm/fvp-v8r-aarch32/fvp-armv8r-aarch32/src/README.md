# `fvp-armv8r-aarch32/src` Component (`boards/arm/fvp-v8r-aarch32/fvp-armv8r-aarch32/src`)

## Overview
Board-level C implementation (`src`) for `fvp-armv8r-aarch32` (`arm/fvp-v8r-aarch32`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 3 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[fvp-armv8r.h:fvp_bringup]` Public declaration `fvp_bringup()`
- `[fvp_boardinit.c:fvp_memory_initialize]` Public function `fvp_memory_initialize()`
- `[fvp_boardinit.c:fvp_board_initialize]` Public function `fvp_board_initialize()`
- `[fvp_boardinit.c:board_late_initialize]` Public function `board_late_initialize()`
- `[fvp_bringup.c:fvp_bringup]` Public function `fvp_bringup()`

## Invariants
- None

## Side Effects
- `[fvp_bringup.c:fvp_bringup]` Initializes/registers kernel devices or filesystems (`nx_mount()`)

## Verification
- Run: `./tools/configure.sh fvp-armv8r-aarch32:nsh && make`
