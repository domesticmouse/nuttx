# `imx93-qsb/src` Component (`boards/arm/imx9/imx93-qsb/src`)

## Overview
Board-level C implementation (`src`) for `imx93-qsb` (`arm/imx9`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 3 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[imx93-qsb.h:imx93_bringup]` Public declaration `imx93_bringup()`
- `[imx93_boardinit.c:imx93_memory_initialize]` Public function `imx93_memory_initialize()`
- `[imx93_boardinit.c:imx9_boardinitialize]` Public function `imx9_boardinitialize()`
- `[imx93_boardinit.c:board_late_initialize]` Public function `board_late_initialize()`
- `[imx93_bringup.c:nsh_consolemain]` Public function `nsh_consolemain()`
- `[imx93_bringup.c:rpmsg_serialrawinit]` Public function `rpmsg_serialrawinit()`
- `[imx93_bringup.c:imx93_bringup]` Public function `imx93_bringup()`

## Invariants
- None

## Side Effects
- `[imx93_bringup.c:nsh_consolemain]` Initializes/registers kernel devices or filesystems (`nx_mount()`)

## Verification
- Run: `./tools/configure.sh imx93-qsb:nsh && make`
