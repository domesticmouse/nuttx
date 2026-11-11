# `hifive1-revb/src` Component (`boards/risc-v/fe310/hifive1-revb/src`)

## Overview
Board-level C implementation (`src`) for `hifive1-revb` (`risc-v/fe310`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[hifive1-revb.h:fe310_bringup]` Public declaration `fe310_bringup()`
- `[fe310_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[fe310_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[fe310_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[fe310_boot.c:fe310_boardinitialize]` Public function `fe310_boardinitialize()`
- `[fe310_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[fe310_bringup.c:fe310_bringup]` Public function `fe310_bringup()`
- `[fe310_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[fe310_buttons.c:board_buttons]` Public function `board_buttons()`
- `[fe310_buttons.c:board_button_irq]` Public function `board_button_irq()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`
- `[fe310_buttons.c:ASSERT]` Requires `id == 0`

## Side Effects
- `[fe310_boot.c:fe310_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[fe310_bringup.c:fe310_bringup]` Initializes/registers kernel devices or filesystems (`btn_lower_initialize()`, `nx_mount()`)
- `[fe310_buttons.c:board_button_initialize]` Modifies interrupt controller or critical-section state

## Verification
- Run: `./tools/configure.sh hifive1-revb:nsh && make`
