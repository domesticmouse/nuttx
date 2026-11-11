# `ekk-lm3s9b96/src` Component (`boards/arm/tiva/ekk-lm3s9b96/src`)

## Overview
Board-level C implementation (`src`) for `ekk-lm3s9b96` (`arm/tiva`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[ekk-lm3s9b96.h:lm_ssidev_initialize]` Public declaration `lm_ssidev_initialize()`
- `[ekk-lm3s9b96.h:LED_GPIO]` Hardware/board configuration macros (`LED_GPIO`)
- `[lm_boot.c:tiva_boardinitialize]` Public function `tiva_boardinitialize()`
- `[lm_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[lm_ethernet.c:tiva_ethernetmac]` Public function `tiva_ethernetmac()`
- `[lm_leds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[lm_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[lm_leds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[lm_ssi.c:lm_ssidev_initialize]` Public function `lm_ssidev_initialize()`
- `[lm_ssi.c:tiva_ssiselect]` Public function `tiva_ssiselect()`
- `[lm_ssi.c:tiva_ssistatus]` Public function `tiva_ssistatus()`

## Invariants
- `[lm_ethernet.c:DEBUGASSERT]` Requires `user0 != 0xffffffff && user1 != 0xffffffff`

## Side Effects
- `[lm_boot.c:tiva_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `lm_ssidev_initialize()`)
- `[lm_leds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[lm_ssi.c:lm_ssidev_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh ekk-lm3s9b96:nsh && make`
