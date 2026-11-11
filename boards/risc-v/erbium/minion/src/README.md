# `minion/src` Component (`boards/risc-v/erbium/minion/src`)

## Overview
Board-level C implementation (`src`) for `minion` (`risc-v/erbium`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 1 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[erbium_bringup.c:board_late_initialize]` Public function `board_late_initialize()`

## Invariants
- None

## Side Effects
- `[erbium_bringup.c:board_late_initialize]` Initializes/registers kernel devices or filesystems (`nx_mount()`)

## Verification
- Run: `./tools/configure.sh minion:nsh && make`
