# `mps3-an547/src` Component (`boards/arm/mps/mps3-an547/src`)

## Overview
Board-level C implementation (`src`) for `mps3-an547` (`arm/mps`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 2 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[mps3_bringup.c:board_boot_image]` Public function `board_boot_image()`
- `[mps3_bringup.c:board_late_initialize]` Public function `board_late_initialize()`
- `[mps3_reset.c:board_reset]` Public function `board_reset()`

## Invariants
- None

## Side Effects
- `[mps3_bringup.c:board_boot_image]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[mps3_bringup.c:board_boot_image]` Initializes/registers kernel devices or filesystems (`libelf_initialize()`, `nx_mount()`, `romdisk_register()`)

## Verification
- Run: `./tools/configure.sh mps3-an547:nsh && make`
