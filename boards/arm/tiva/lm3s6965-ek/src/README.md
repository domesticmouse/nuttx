# `lm3s6965-ek/src` Component (`boards/arm/tiva/lm3s6965-ek/src`)

## Overview
Board-level C implementation (`src`) for `lm3s6965-ek` (`arm/tiva`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[lm3s6965-ek.h:lm_bringup]` Public declaration `lm_bringup()`
- `[lm3s6965-ek.h:lm_ssidev_initialize]` Public declaration `lm_ssidev_initialize()`
- `[lm3s6965-ek.h:SDCCS_GPIO]` Hardware/board configuration macros (`SDCCS_GPIO`, `LED_GPIO`, `OLEDDC_GPIO`, `OLEDCS_GPIO`, `OLEDEN_GPIO`, `LM_PROCFS_MOUNTPOINT`)
- `[lm_boot.c:tiva_boardinitialize]` Public function `tiva_boardinitialize()`
- `[lm_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[lm_bringup.c:lm_bringup]` Public function `lm_bringup()`
- `[lm_ethernet.c:tiva_ethernetmac]` Public function `tiva_ethernetmac()`
- `[lm_leds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[lm_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[lm_leds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[lm_oled.c:board_graphics_setup]` Public function `board_graphics_setup()`
- `[lm_oled.c:tiva_ssicmddata]` Public function `tiva_ssicmddata()`
- `[lm_ssi.c:lm_ssidev_initialize]` Public function `lm_ssidev_initialize()`
- `[lm_ssi.c:tiva_ssiselect]` Public function `tiva_ssiselect()`
- `[lm_ssi.c:tiva_ssistatus]` Public function `tiva_ssistatus()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_BOARDCTL`, `CONFIG_BOARD_LATE_INITIALIZE`, `CONFIG_NX_LCDDRIVER`
- `[lm_bringup.c:lm_bringup]` Validates preconditions and returns `-ENODEV` on failure
- `[lm_ethernet.c:DEBUGASSERT]` Requires `user0 != 0xffffffff && user1 != 0xffffffff`
- `[lm_oled.c:board_graphics_setup]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[lm_boot.c:tiva_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `lm_ssidev_initialize()`)
- `[lm_bringup.c:lm_bringup]` Initializes/registers kernel devices or filesystems (`nx_mount()`, `tiva_ssibus_initialize()`)
- `[lm_leds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[lm_oled.c:board_graphics_setup]` Configures or drives hardware GPIO pins
- `[lm_oled.c:board_graphics_setup]` Initializes/registers kernel devices or filesystems (`rit_initialize()`, `tiva_ssibus_initialize()`)
- `[lm_ssi.c:lm_ssidev_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh lm3s6965-ek:nsh && make`
