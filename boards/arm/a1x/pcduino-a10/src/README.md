# `pcduino-a10/src` Component (`boards/arm/a1x/pcduino-a10/src`)

## Overview
Board-level C implementation (`src`) for `pcduino-a10` (`arm/a1x`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[pcduino_a10.h:a1x_bringup]` Public declaration `a1x_bringup()`
- `[pcduino_a10.h:a1x_led_initialize]` Public declaration `a1x_led_initialize()`
- `[pcduino_a10.h:PIO_LED1]` Hardware/board configuration macros (`PIO_LED1`, `PIO_LED3`, `PIO_LED4`, `PIO_KEY_BACK`, `PIO_KEY_HOME`, `PIO_KEY_MENU`)
- `[a1x_boot.c:a1x_boardinitialize]` Public function `a1x_boardinitialize()`
- `[a1x_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[a1x_bringup.c:a1x_bringup]` Public function `a1x_bringup()`
- `[a1x_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[a1x_buttons.c:board_buttons]` Public function `board_buttons()`
- `[a1x_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[a1x_leds.c:a1x_led_initialize]` Public function `a1x_led_initialize()`
- `[a1x_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[a1x_leds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[a1x_leds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[a1x_leds.c:board_userled]` Public function `board_userled()`
- `[a1x_leds.c:board_userled_all]` Public function `board_userled_all()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`
- `[a1x_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure

## Side Effects
- `[a1x_boot.c:a1x_boardinitialize]` Initializes/registers kernel devices or filesystems (`a1x_led_initialize()`)
- `[a1x_bringup.c:a1x_bringup]` Initializes/registers kernel devices or filesystems (`btn_lower_initialize()`, `nx_mount()`, `userled_lower_initialize()`)
- `[a1x_buttons.c:board_button_initialize]` Modifies interrupt controller or critical-section state

## Verification
- Run: `./tools/configure.sh pcduino-a10:nsh && make`
