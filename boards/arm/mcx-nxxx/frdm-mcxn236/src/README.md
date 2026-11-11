# `frdm-mcxn236/src` Component (`boards/arm/mcx-nxxx/frdm-mcxn236/src`)

## Overview
Board-level C implementation (`src`) for `frdm-mcxn236` (`arm/mcx-nxxx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 3 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[frdm-mcxn236.h:n23x_bringup]` Public declaration `n23x_bringup()`
- `[n23x_boardinit.c:nxxx_boardinitialize]` Public function `nxxx_boardinitialize()`
- `[n23x_boardinit.c:board_late_initialize]` Public function `board_late_initialize()`
- `[n23x_bringup.c:n23x_bringup]` Public function `n23x_bringup()`

## Invariants
- None

## Side Effects
- `[n23x_bringup.c:n23x_bringup]` Initializes/registers kernel devices or filesystems (`nx_mount()`)

## Verification
- Run: `./tools/configure.sh frdm-mcxn236:nsh && make`
