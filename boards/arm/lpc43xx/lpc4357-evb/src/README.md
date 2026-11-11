# `lpc4357-evb/src` Component (`boards/arm/lpc43xx/lpc4357-evb/src`)

## Overview
Board-level C implementation (`src`) for `lpc4357-evb` (`arm/lpc43xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[lpc4357-evb.h:PINCONFIG_LED]` Hardware/board configuration macros (`PINCONFIG_LED`, `GPIO_LED`)
- `[lpc43_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[lpc43_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[lpc43_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[lpc43_boot.c:lpc43_boardinitialize]` Public function `lpc43_boardinitialize()`
- `[lpc43_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[lpc43_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[lpc43_buttons.c:board_buttons]` Public function `board_buttons()`
- `[lpc43_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[lpc43_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[lpc43_userleds.c:board_userled]` Public function `board_userled()`
- `[lpc43_userleds.c:board_userled_all]` Public function `board_userled_all()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_SPIFI_LIBRARY`, `CONFIG_USBMSC`
- `[lpc43_boot.c:lpc43_boardinitialize]` Validates preconditions and returns `-ENODEV` on failure
- `[lpc43_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL`, `-ENOSYS` on failure

## Side Effects
- `[lpc4357-evb.h:lpc4357-evb.h]` Configures or drives hardware GPIO pins
- `[lpc43_boot.c:lpc43_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `lpc43_spifi_initialize()`, `nsh_spifi_initialize()`, `nx_mount()`, `nxffs_initialize()`)
- `[lpc43_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[lpc43_buttons.c:board_button_initialize]` Modifies interrupt controller or critical-section state

## Verification
- Run: `./tools/configure.sh lpc4357-evb:nsh && make`
