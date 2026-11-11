# `hpm6750evk2/src` Component (`boards/risc-v/hpm6750/hpm6750evk2/src`)

## Overview
Board-level C implementation (`src`) for `hpm6750evk2` (`risc-v/hpm6750`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 3 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[hpm6750evk2.h:hpm6750_bringup]` Public declaration `hpm6750_bringup()`
- `[hpm6750_boot.c:hpm6750_boardinitialize]` Public function `hpm6750_boardinitialize()`
- `[hpm6750_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[hpm6750_bringup.c:hpm6750_bringup]` Public function `hpm6750_bringup()`

## Invariants
- None

## Side Effects
- `[hpm6750_bringup.c:hpm6750_bringup]` Initializes/registers kernel devices or filesystems (`nx_mount()`)

## Verification
- Run: `./tools/configure.sh hpm6750evk2:nsh && make`
