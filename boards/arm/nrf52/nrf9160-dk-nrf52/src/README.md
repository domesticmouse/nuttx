# `nrf9160-dk-nrf52/src` Component (`boards/arm/nrf52/nrf9160-dk-nrf52/src`)

## Overview
Board-level C implementation (`src`) for `nrf9160-dk-nrf52` (`arm/nrf52`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 3 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[nrf9160-dk-nrf52.h:nrf52_bringup]` Public declaration `nrf52_bringup()`
- `[nrf9160-dk-nrf52.h:NRF52_PROCFS_MOUNTPOINT]` Hardware/board configuration macros (`NRF52_PROCFS_MOUNTPOINT`)
- `[nrf52_boot.c:nrf52_board_initialize]` Public function `nrf52_board_initialize()`
- `[nrf52_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[nrf52_bringup.c:nrf52_bringup]` Public function `nrf52_bringup()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`

## Side Effects
- `[nrf52_boot.c:nrf52_board_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[nrf52_bringup.c:nrf52_bringup]` Initializes/registers kernel devices or filesystems (`nrf52_ieee802154_initialize()`, `nx_mount()`)

## Verification
- Run: `./tools/configure.sh nrf9160-dk-nrf52:nsh && make`
