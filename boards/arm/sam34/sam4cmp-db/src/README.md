# `sam4cmp-db/src` Component (`boards/arm/sam34/sam4cmp-db/src`)

## Overview
Board-level C implementation (`src`) for `sam4cmp-db` (`arm/sam34`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 3 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[sam4cmp-db.h:sam_bringup]` Public declaration `sam_bringup()`
- `[sam_boot.c:sam_boardinitialize]` Public function `sam_boardinitialize()`
- `[sam_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[sam_bringup.c:sam_bringup]` Public function `sam_bringup()`

## Invariants
- None

## Side Effects
- `[sam_bringup.c:sam_bringup]` Initializes/registers kernel devices or filesystems (`nx_mount()`)

## Verification
- Run: `./tools/configure.sh sam4cmp-db:nsh && make`
