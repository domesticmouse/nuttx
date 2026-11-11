# `ab32vg1-generic/src` Component (`boards/risc-v/ab32vg1/ab32vg1-generic/src`)

## Overview
Board-level C implementation (`src`) for `ab32vg1-generic` (`risc-v/ab32vg1`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[ab32vg1-generic.h:ab32vg1_bringup]` Public declaration `ab32vg1_bringup()`
- `[ab32vg1-generic.h:GPIO_LED_RED]` Hardware/board configuration macros (`GPIO_LED_RED`, `GPIO_LED_GREEN`, `GPIO_LED_BLUE`, `GPIO_KEY1`, `GPIO_KEY2`)
- `[ab32vg1_appinit.c:board_app_initialize]` Public function `board_app_initialize()`
- `[ab32vg1_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[ab32vg1_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[ab32vg1_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[ab32vg1_boot.c:ab32vg1_boardinitialize]` Public function `ab32vg1_boardinitialize()`
- `[ab32vg1_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[ab32vg1_bringup.c:ab32vg1_bringup]` Public function `ab32vg1_bringup()`
- `[ab32vg1_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[ab32vg1_buttons.c:board_buttons]` Public function `board_buttons()`
- `[ab32vg1_reset.c:board_reset]` Public function `board_reset()`
- `[ab32vg1_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[ab32vg1_userleds.c:board_userled]` Public function `board_userled()`
- `[ab32vg1_userleds.c:board_userled_all]` Public function `board_userled_all()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_BOARDCTL`, `CONFIG_BOARDCTL_RESET`, `CONFIG_USERLED`

## Side Effects
- `[ab32vg1_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[ab32vg1_boot.c:ab32vg1_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[ab32vg1_bringup.c:ab32vg1_bringup]` Initializes/registers kernel devices or filesystems (`btn_lower_initialize()`, `nx_mount()`, `userled_lower_initialize()`)
- `[ab32vg1_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[ab32vg1_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh ab32vg1-generic:nsh && make`
