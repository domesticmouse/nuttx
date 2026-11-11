# `sabre-6quad/src` Component (`boards/arm/imx6/sabre-6quad/src`)

## Overview
Board-level C implementation (`src`) for `sabre-6quad` (`arm/imx6`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[sabre-6quad.h:imx_bringup]` Public declaration `imx_bringup()`
- `[sabre-6quad.h:IOMUX_LED]` Hardware/board configuration macros (`IOMUX_LED`, `GPIO_LED`)
- `[imx_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[imx_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[imx_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[imx_boardinit.c:imx_memory_initialize]` Public function `imx_memory_initialize()`
- `[imx_boardinit.c:imx_board_initialize]` Public function `imx_board_initialize()`
- `[imx_boardinit.c:board_late_initialize]` Public function `board_late_initialize()`
- `[imx_bringup.c:imx_bringup]` Public function `imx_bringup()`
- `[imx_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[imx_userleds.c:board_userled]` Public function `board_userled()`
- `[imx_userleds.c:board_userled_all]` Public function `board_userled_all()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_LEDS`

## Side Effects
- `[imx_boardinit.c:imx_memory_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[imx_bringup.c:imx_bringup]` Initializes/registers kernel devices or filesystems (`nx_mount()`)

## Verification
- Run: `./tools/configure.sh sabre-6quad:nsh && make`
