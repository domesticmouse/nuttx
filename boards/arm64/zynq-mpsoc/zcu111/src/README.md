# `zcu111/src` Component (`boards/arm64/zynq-mpsoc/zcu111/src`)

## Overview
Board-level C implementation (`src`) for `zcu111` (`arm64/zynq-mpsoc`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[zcu111.h:zcu111_bringup]` Public declaration `zcu111_bringup()`
- `[zcu111.h:LED_DS50]` Hardware/board configuration macros (`LED_DS50`)
- `[zcu111_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[zcu111_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[zcu111_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[zcu111_boardinit.c:zynq_memory_initialize]` Public function `zynq_memory_initialize()`
- `[zcu111_boardinit.c:zynq_board_initialize]` Public function `zynq_board_initialize()`
- `[zcu111_boardinit.c:board_late_initialize]` Public function `board_late_initialize()`
- `[zcu111_bringup.c:zcu111_bringup]` Public function `zcu111_bringup()`
- `[zcu111_ethernet.c:zynq_phyread_mmd_indirect]` Public function `zynq_phyread_mmd_indirect()`
- `[zcu111_ethernet.c:zynq_phywrite_mmd_indirect]` Public function `zynq_phywrite_mmd_indirect()`
- `[zcu111_ethernet.c:zynq_phy_boardinitialize]` Public function `zynq_phy_boardinitialize()`
- `[zcu111_reset.c:board_reset]` Public function `board_reset()`
- `[zcu111_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[zcu111_userleds.c:board_userled]` Public function `board_userled()`
- `[zcu111_userleds.c:board_userled_all]` Public function `board_userled_all()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_LEDS`, `CONFIG_BOARDCTL_RESET`, `CONFIG_ETC_ROMFS`, `CONFIG_NET`, `CONFIG_USERLED`
- `[zcu111_ethernet.c:zynq_phyread_mmd_indirect]` Validates preconditions and returns `-ENOMEM` on failure

## Side Effects
- `[zcu111_boardinit.c:zynq_memory_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `zynq_mio_initialize()`)
- `[zcu111_bringup.c:zcu111_bringup]` Initializes/registers kernel devices or filesystems (`userled_lower_initialize()`)

## Verification
- Run: `./tools/configure.sh zcu111:nsh && make`
