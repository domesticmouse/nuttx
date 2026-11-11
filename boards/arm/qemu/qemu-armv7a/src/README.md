# `qemu-armv7a/src` Component (`boards/arm/qemu/qemu-armv7a/src`)

## Overview
Board-level C implementation (`src`) for `qemu-armv7a` (`arm/qemu`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 3 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[qemu-armv7a.h:qemu_bringup]` Public declaration `qemu_bringup()`
- `[qemu_boardinit.c:qemu_memory_initialize]` Public function `qemu_memory_initialize()`
- `[qemu_boardinit.c:qemu_board_initialize]` Public function `qemu_board_initialize()`
- `[qemu_boardinit.c:board_late_initialize]` Public function `board_late_initialize()`
- `[qemu_boardinit.c:board_power_off]` Public function `board_power_off()`
- `[qemu_bringup.c:qemu_bringup]` Public function `qemu_bringup()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ETC_ROMFS`, `CONFIG_LIBC_FDT`, `CONFIG_SYSTEM_NXINIT`
- `[qemu_bringup.c:qemu_bringup]` Validates preconditions and returns `-EINVAL` on failure

## Side Effects
- `[qemu_bringup.c:qemu_bringup]` Initializes/registers kernel devices or filesystems (`fdt_cfi_register()`, `fdt_pci_ecam_register()`, `fdt_virtio_mmio_devices_register()`, `nx_mount()`, `rpmsg_port_uart_initialize()`)

## Verification
- Run: `./tools/configure.sh qemu-armv7a:nsh && make`
