# `qemu-intel64/src` Component (`boards/x86_64/qemu/qemu-intel64/src`)

## Overview
Board-level C implementation (`src`) for `qemu-intel64` (`x86_64/qemu`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 9 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[qemu_intel64.h:qemu_bringup]` Public declaration `qemu_bringup()`
- `[romfs.h]` Board header declarations `romfs.h`
- `[qemu_boardinit.c:board_late_initialize]` Public function `board_late_initialize()`
- `[qemu_boot.c:x86_64_boardinitialize]` Public function `x86_64_boardinitialize()`
- `[qemu_bringup.c:qemu_bringup]` Public function `qemu_bringup()`
- `[qemu_net.c:x86_64_netinitialize]` Public function `x86_64_netinitialize()`
- `[qemu_power.c:board_power_off]` Public function `board_power_off()`
- `[qemu_reset.c:board_reset]` Public function `board_reset()`
- `[romfs_stub.c:romfs_img]` Module symbol `romfs_img`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_BOARDCTL_POWEROFF`, `CONFIG_BOARDCTL_RESET`, `CONFIG_ETC_ROMFS`, `CONFIG_SYSTEM_NXINIT`
- `[qemu_boardinit.c:#error]` Compile-time guard: `KERNEL build require CONFIG_BOARD_LATE_INITIALIZE`
- `[qemu_bringup.c:#error]` Compile-time guard: `this logic requires that HPET_ALARM_CHAN is set to 0`

## Side Effects
- `[qemu_boardinit.c:board_late_initialize]` Initializes/registers kernel devices or filesystems (`romdisk_register()`)
- `[qemu_boot.c:x86_64_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[qemu_bringup.c:qemu_bringup]` Initializes/registers kernel devices or filesystems (`fb_register()`, `nx_mount()`, `oneshot_initialize()`, `oneshot_register()`)

## Verification
- Run: `./tools/configure.sh qemu-intel64:nsh && make`
