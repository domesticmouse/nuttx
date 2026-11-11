# `imx8qm-mek/src` Component (`boards/arm64/imx8/imx8qm-mek/src`)

## Overview
Board-level C implementation (`src`) for `imx8qm-mek` (`arm64/imx8`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 3 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[imx8qm-mek.h:imx8_bringup]` Public declaration `imx8_bringup()`
- `[imx8_boardinit.c:imx8_memory_initialize]` Public function `imx8_memory_initialize()`
- `[imx8_boardinit.c:imx8_board_initialize]` Public function `imx8_board_initialize()`
- `[imx8_boardinit.c:board_late_initialize]` Public function `board_late_initialize()`
- `[imx8_bringup.c:imx8_bringup]` Public function `imx8_bringup()`

## Invariants
- None

## Side Effects
- `[imx8_bringup.c:imx8_bringup]` Initializes/registers kernel devices or filesystems (`nx_mount()`)

## Verification
- Run: `./tools/configure.sh imx8qm-mek:nsh && make`
