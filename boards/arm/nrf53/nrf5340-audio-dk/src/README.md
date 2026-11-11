# `nrf5340-audio-dk/src` Component (`boards/arm/nrf53/nrf5340-audio-dk/src`)

## Overview
Board-level C implementation (`src`) for `nrf5340-audio-dk` (`arm/nrf53`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[nrf5340-audio-dk.h:nrf53_bringup]` Public declaration `nrf53_bringup()`
- `[nrf5340-audio-dk.h:GPIO_LED1]` Hardware/board configuration macros (`GPIO_LED1`, `GPIO_LED2`, `GPIO_LED3`, `GPIO_BUTTON1`, `GPIO_BUTTON2`, `GPIO_BUTTON3` (+2 more))
- `[nrf53_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[nrf53_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[nrf53_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[nrf53_boot.c:nrf53_board_initialize]` Public function `nrf53_board_initialize()`
- `[nrf53_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[nrf53_bringup.c:nrf53_bringup]` Public function `nrf53_bringup()`
- `[nrf53_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[nrf53_userleds.c:board_userled]` Public function `board_userled()`
- `[nrf53_userleds.c:board_userled_all]` Public function `board_userled_all()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_LEDS`

## Side Effects
- `[nrf53_boot.c:nrf53_board_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[nrf53_bringup.c:nrf53_bringup]` Initializes/registers kernel devices or filesystems (`userled_lower_initialize()`)

## Verification
- Run: `./tools/configure.sh nrf5340-audio-dk:nsh_cpuapp && make`
