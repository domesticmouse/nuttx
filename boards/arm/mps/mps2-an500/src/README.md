# `mps2-an500/src` Component (`boards/arm/mps/mps2-an500/src`)

## Overview
Board-level C implementation (`src`) for `mps2-an500` (`arm/mps`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 2 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[mps2_bringup.c:board_late_initialize]` Public function `board_late_initialize()`
- `[mps2_reset.c:board_reset]` Public function `board_reset()`

## Invariants
- None

## Side Effects
- `[mps2_bringup.c:board_late_initialize]` Initializes/registers kernel devices or filesystems (`nx_mount()`, `rammtd_initialize()`)

## Verification
- Run: `./tools/configure.sh mps2-an500:nsh && make`
