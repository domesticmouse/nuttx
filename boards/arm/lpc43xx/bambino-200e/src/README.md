# `bambino-200e/src` Component (`boards/arm/lpc43xx/bambino-200e/src`)

## Overview
Board-level C implementation (`src`) for `bambino-200e` (`arm/lpc43xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[bambino-200e.h:lpc43_sspdev_initialize]` Public declaration `lpc43_sspdev_initialize()`
- `[bambino-200e.h:lpc43_max31855initialize]` Public declaration `lpc43_max31855initialize()`
- `[bambino-200e.h:lpc43_timerinitialize]` Public declaration `lpc43_timerinitialize()`
- `[bambino-200e.h:HAVE_MMCSD]` Hardware/board configuration macros (`HAVE_MMCSD`, `PINCONFIG_LED1`, `PINCONFIG_LED2`, `GPIO_LED1`, `GPIO_LED2`, `BAMBINO_BUT1` (+11 more))
- `[lpc43_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[lpc43_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[lpc43_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[lpc43_boot.c:lpc43_boardinitialize]` Public function `lpc43_boardinitialize()`
- `[lpc43_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[lpc43_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[lpc43_buttons.c:board_buttons]` Public function `board_buttons()`
- `[lpc43_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[lpc43_max31855.c:lpc43_max31855initialize]` Public function `lpc43_max31855initialize()`
- `[lpc43_ssp.c:lpc43_sspdev_initialize]` Public function `lpc43_sspdev_initialize()`
- `[lpc43_ssp.c:lpc43_ssp0select]` Public function `lpc43_ssp0select()`
- `[lpc43_ssp.c:lpc43_ssp0status]` Public function `lpc43_ssp0status()`
- `[lpc43_ssp.c:lpc43_ssp1select]` Public function `lpc43_ssp1select()`
- `[lpc43_ssp.c:lpc43_ssp1status]` Public function `lpc43_ssp1status()`
- `[lpc43_timer.c:lpc43_timerinitialize]` Public function `lpc43_timerinitialize()`
- `[lpc43_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[lpc43_userleds.c:board_userled]` Public function `board_userled()`
- `[lpc43_userleds.c:board_userled_all]` Public function `board_userled_all()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_SENSORS_MAX31855`, `CONFIG_SPIFI_LIBRARY`, `CONFIG_TIMER`, `CONFIG_USBMSC`
- `[lpc43_boot.c:lpc43_boardinitialize]` Validates preconditions and returns `-ENODEV` on failure
- `[lpc43_max31855.c:lpc43_max31855initialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[bambino-200e.h:lpc43_sspdev_initialize]` Configures or drives hardware GPIO pins
- `[lpc43_boot.c:lpc43_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `lpc43_sdmmc_initialize()`, `lpc43_spifi_initialize()`, `lpc43_sspdev_initialize()`, `nsh_spifi_initialize()`)
- `[lpc43_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[lpc43_buttons.c:board_button_initialize]` Modifies interrupt controller or critical-section state
- `[lpc43_max31855.c:lpc43_max31855initialize]` Initializes/registers kernel devices or filesystems (`lpc43_sspbus_initialize()`, `max31855_register()`)

## Verification
- Run: `./tools/configure.sh bambino-200e:nsh && make`
