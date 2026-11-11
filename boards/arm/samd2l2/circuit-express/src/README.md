# `circuit-express/src` Component (`boards/arm/samd2l2/circuit-express/src`)

## Overview
Board-level C implementation (`src`) for `circuit-express` (`arm/samd2l2`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[circuit_express.h:sam_bringup]` Public declaration `sam_bringup()`
- `[circuit_express.h:PORT_STATUS_LED]` Hardware/board configuration macros (`PORT_STATUS_LED`)
- `[sam_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[sam_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[sam_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[sam_boot.c:sam_boardinitialize]` Public function `sam_boardinitialize()`
- `[sam_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[sam_bringup.c:sam_bringup]` Public function `sam_bringup()`
- `[sam_usb.c:sam_usbinitialize]` Public function `sam_usbinitialize()`
- `[sam_usb.c:sam_usb_suspend]` Public function `sam_usb_suspend()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_USBDEV`

## Side Effects
- `[sam_boot.c:sam_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)

## Verification
- Run: `./tools/configure.sh circuit-express:nsh && make`
