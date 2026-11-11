# `same54-xplained-pro/src` Component (`boards/arm/samd5e5/same54-xplained-pro/src`)

## Overview
Board-level C implementation (`src`) for `same54-xplained-pro` (`arm/samd5e5`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 6 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[same54-xplained-pro.h:sam_bringup]` Public declaration `sam_bringup()`
- `[same54-xplained-pro.h:sam_led_pminitialize]` Public declaration `sam_led_pminitialize()`
- `[same54-xplained-pro.h:PORT_LED0]` Hardware/board configuration macros (`PORT_LED0`, `PORT_PHY_RESET`)
- `[sam_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[sam_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[sam_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[sam_autoleds.c:sam_led_pminitialize]` Public function `sam_led_pminitialize()`
- `[sam_boot.c:sam_board_initialize]` Public function `sam_board_initialize()`
- `[sam_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[sam_bringup.c:sam_bringup]` Public function `sam_bringup()`
- `[sam_phyinit.c:sam_phy_boardinitialize]` Public function `sam_phy_boardinitialize()`
- `[sam_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[sam_userleds.c:board_userled]` Public function `board_userled()`
- `[sam_userleds.c:board_userled_all]` Public function `board_userled_all()`
- `[sam_userleds.c:sam_led_pminitialize]` Public function `sam_led_pminitialize()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_LEDS`, `CONFIG_SAMD5E5_GMAC_PHYINIT`

## Side Effects
- `[sam_autoleds.c:board_autoled_initialize]` Initializes/registers kernel devices or filesystems (`pm_register()`)
- `[sam_boot.c:sam_board_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[sam_bringup.c:sam_bringup]` Initializes/registers kernel devices or filesystems (`nx_mount()`)
- `[sam_userleds.c:board_userled_initialize]` Initializes/registers kernel devices or filesystems (`pm_register()`)

## Verification
- Run: `./tools/configure.sh same54-xplained-pro:nsh && make`
