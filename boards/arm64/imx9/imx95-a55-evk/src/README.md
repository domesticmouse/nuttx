# `imx95-a55-evk/src` Component (`boards/arm64/imx9/imx95-a55-evk/src`)

## Overview
Board-level C implementation (`src`) for `imx95-a55-evk` (`arm64/imx9`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[imx95-evk.h:imx9_bringup]` Public declaration `imx9_bringup()`
- `[imx95-evk.h:imx9_pwm_setup]` Public declaration `imx9_pwm_setup()`
- `[imx95-evk.h:imx9_i2c_initialize]` Public declaration `imx9_i2c_initialize()`
- `[imx95-evk.h:imx9_spi_initialize]` Public declaration `imx9_spi_initialize()`
- `[imx95-evk.h:imx9_usdhc_init]` Public declaration `imx9_usdhc_init()`
- `[imx95-evk.h:SDIO_SLOTNO]` Hardware/board configuration macros (`SDIO_SLOTNO`, `SDIO_MINOR`)
- `[imx9_boardinit.c:imx9_memory_initialize]` Public function `imx9_memory_initialize()`
- `[imx9_boardinit.c:imx9_board_initialize]` Public function `imx9_board_initialize()`
- `[imx9_boardinit.c:board_late_initialize]` Public function `board_late_initialize()`
- `[imx9_bringup.c:imx9_bringup]` Public function `imx9_bringup()`
- `[imx9_reset.c:board_reset]` Public function `board_reset()`
- `[imx9_usdhc.c:imx9_usdhc_init]` Public function `imx9_usdhc_init()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_BOARDCTL_RESET`, `CONFIG_IMX9_USDHC`
- `[imx9_usdhc.c:imx9_usdhc_init]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[imx9_bringup.c:imx9_bringup]` Initializes/registers kernel devices or filesystems (`nx_mount()`)
- `[imx9_usdhc.c:imx9_usdhc_init]` Initializes/registers kernel devices or filesystems (`imx9_usdhc_initialize()`)

## Verification
- Run: `./tools/configure.sh imx95-a55-evk:nsh && make`
