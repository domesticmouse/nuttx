# `rv-virt/src` Component (`boards/risc-v/qemu-rv/rv-virt/src`)

## Overview
Board-level C implementation (`src`) for `rv-virt` (`risc-v/qemu-rv`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[romfs.h]` Board header declarations `romfs.h`
- `[qemu_rv_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[qemu_rv_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[qemu_rv_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[qemu_rv_boardinit.c:board_late_initialize]` Public function `board_late_initialize()`
- `[qemu_rv_boardinit.c:board_early_initialize]` Public function `board_early_initialize()`
- `[qemu_rv_boardinit.c:board_power_off]` Public function `board_power_off()`
- `[qemu_rv_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[qemu_rv_userleds.c:board_userled]` Public function `board_userled()`
- `[qemu_rv_userleds.c:board_userled_all]` Public function `board_userled_all()`
- `[romfs_stub.c:romfs_img]` Module symbol `romfs_img`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_LEDS`, `CONFIG_BUILD_KERNEL`, `CONFIG_ETC_ROMFS`, `CONFIG_RISCV_SEMIHOSTING_HOSTFS`, `CONFIG_SYSTEM_NXINIT`, `CONFIG_USERLED`

## Side Effects
- `[qemu_rv_boardinit.c:board_late_initialize]` Initializes/registers kernel devices or filesystems (`romdisk_register()`, `userled_lower_initialize()`)

## Verification
- Run: `./tools/configure.sh rv-virt:nsh && make`
