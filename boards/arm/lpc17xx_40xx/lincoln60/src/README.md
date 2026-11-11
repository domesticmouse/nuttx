# `lincoln60/src` Component (`boards/arm/lpc17xx_40xx/lincoln60/src`)

## Overview
Board-level C implementation (`src`) for `lincoln60` (`arm/lpc17xx_40xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[lincoln60.h:lincoln60_sspdev_initialize]` Public declaration `lincoln60_sspdev_initialize()`
- `[lincoln60.h:LINCOLN60_LED1]` Hardware/board configuration macros (`LINCOLN60_LED1`, `LINCOLN60_LED1_OFF`, `LINCOLN60_LED1_ON`, `LINCOLN60_LED2`, `LINCOLN60_LED2_OFF`, `LINCOLN60_LED2_ON` (+4 more))
- `[lpc17_40_boot.c:lpc17_40_boardinitialize]` Public function `lpc17_40_boardinitialize()`
- `[lpc17_40_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[lpc17_40_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[lpc17_40_buttons.c:board_buttons]` Public function `board_buttons()`
- `[lpc17_40_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[lpc17_40_leds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[lpc17_40_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[lpc17_40_leds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[lpc17_40_leds.c:lpc17_40_led]` Public function `lpc17_40_led()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_USBMSC`

## Side Effects
- `[lpc17_40_boot.c:lpc17_40_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[lpc17_40_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[lpc17_40_buttons.c:board_button_initialize]` Modifies interrupt controller or critical-section state
- `[lpc17_40_leds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh lincoln60:nsh && make`
