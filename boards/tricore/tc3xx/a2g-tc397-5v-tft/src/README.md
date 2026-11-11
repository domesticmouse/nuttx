# `a2g-tc397-5v-tft/src` Component (`boards/tricore/tc3xx/a2g-tc397-5v-tft/src`)

## Overview
Board-level C implementation (`src`) for `a2g-tc397-5v-tft` (`tricore/tc3xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 3 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[tc397.h:tc397_bringup]` Public declaration `tc397_bringup()`
- `[tc397_boardinit.c:tc397_memory_initialize]` Public function `tc397_memory_initialize()`
- `[tc397_boardinit.c:tc397_board_initialize]` Public function `tc397_board_initialize()`
- `[tc397_boardinit.c:board_late_initialize]` Public function `board_late_initialize()`
- `[tc397_bringup.c:tc397_bringup]` Public function `tc397_bringup()`

## Invariants
- None

## Side Effects
- `[tc397_boardinit.c:tc397_memory_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[tc397_bringup.c:tc397_bringup]` Initializes/registers kernel devices or filesystems (`nx_mount()`)

## Verification
- Run: `./tools/configure.sh a2g-tc397-5v-tft:nsh && make`
