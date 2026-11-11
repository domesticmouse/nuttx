# `thingy91-nrf52/src` Component (`boards/arm/nrf52/thingy91-nrf52/src`)

## Overview
Board-level C implementation (`src`) for `thingy91-nrf52` (`arm/nrf52`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[thingy91-nrf52.h:nrf52_bringup]` Public declaration `nrf52_bringup()`
- `[nrf52_boot.c:nrf52_board_initialize]` Public function `nrf52_board_initialize()`
- `[nrf52_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[nrf52_bringup.c:nrf52_bringup]` Public function `nrf52_bringup()`
- `[nrf52_composite.c:board_composite0_connect]` Public function `board_composite0_connect()`
- `[nrf52_composite.c:board_composite_initialize]` Public function `board_composite_initialize()`
- `[nrf52_composite.c:board_composite_connect]` Public function `board_composite_connect()`
- `[nrf52_usb.c:nrf52_usbsuspend]` Public function `nrf52_usbsuspend()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_USBDEV`, `CONFIG_USBDEV_COMPOSITE`
- `[nrf52_composite.c:DEBUGASSERT]` Requires `epin <= NRF52_NENDPOINTS`
- `[nrf52_composite.c:DEBUGASSERT]` Requires `epout <= NRF52_NENDPOINTS`

## Side Effects
- `[nrf52_boot.c:nrf52_board_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[nrf52_composite.c:board_composite0_connect]` Initializes/registers kernel devices or filesystems (`composite_initialize()`)

## Verification
- Run: `./tools/configure.sh thingy91-nrf52:usbnsh && make`
