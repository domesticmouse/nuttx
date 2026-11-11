# `rv32m1-vega/src` Component (`boards/risc-v/rv32m1/rv32m1-vega/src`)

## Overview
Board-level C implementation (`src`) for `rv32m1-vega` (`risc-v/rv32m1`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[rv32m1-vega.h:rv32m1_bringup]` Public declaration `rv32m1_bringup()`
- `[rv32m1-vega.h:BOARD_NBUTTON]` Hardware/board configuration macros (`BOARD_NBUTTON`, `BUTTON_SW2`, `BUTTON_SW3`, `BUTTON_SW4`, `BUTTON_SW5`)
- `[rv32m1_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[rv32m1_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[rv32m1_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[rv32m1_boot.c:rv32m1_boardinitialize]` Public function `rv32m1_boardinitialize()`
- `[rv32m1_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[rv32m1_bringup.c:rv32m1_bringup]` Public function `rv32m1_bringup()`
- `[rv32m1_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[rv32m1_buttons.c:board_buttons]` Public function `board_buttons()`
- `[rv32m1_buttons.c:board_button_irq]` Public function `board_button_irq()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`
- `[rv32m1_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure

## Side Effects
- `[rv32m1_boot.c:rv32m1_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[rv32m1_bringup.c:rv32m1_bringup]` Initializes/registers kernel devices or filesystems (`btn_lower_initialize()`, `nx_mount()`)

## Verification
- Run: `./tools/configure.sh rv32m1-vega:nsh && make`
