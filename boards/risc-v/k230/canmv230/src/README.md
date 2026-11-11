# `canmv230/src` Component (`boards/risc-v/k230/canmv230/src`)

## Overview
Board-level C implementation (`src`) for `canmv230` (`risc-v/k230`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 3 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[romfs.h]` Board header declarations `romfs.h`
- `[canmv_init.c:board_reset]` Public function `board_reset()`
- `[canmv_init.c:rpmsg_serialinit]` Public function `rpmsg_serialinit()`
- `[canmv_init.c:board_late_initialize]` Public function `board_late_initialize()`
- `[romfs_stub.c:romfs_img]` Module symbol `romfs_img`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_BUILD_KERNEL`

## Side Effects
- `[canmv_init.c:board_reset]` Initializes/registers kernel devices or filesystems (`romdisk_register()`)

## Verification
- Run: `./tools/configure.sh canmv230:nsh && make`
