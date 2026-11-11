# `freedom-k66f/src` Component (`boards/arm/kinetis/freedom-k66f/src`)

## Overview
Board-level C implementation (`src`) for `freedom-k66f` (`arm/kinetis`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 15 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[freedom-k66f.h:k66_spidev_initialize]` Public declaration `k66_spidev_initialize()`
- `[freedom-k66f.h:k66_rtc_initialize]` Public declaration `k66_rtc_initialize()`
- `[freedom-k66f.h:k66_usbinitialize]` Public declaration `k66_usbinitialize()`
- `[freedom-k66f.h:k66_bringup]` Public declaration `k66_bringup()`
- `[freedom-k66f.h:k66_sdhc_initialize]` Public declaration `k66_sdhc_initialize()`
- `[freedom-k66f.h:k66_cardinserted]` Public declaration `k66_cardinserted()`
- `[freedom-k66f.h:k66_writeprotected]` Public declaration `k66_writeprotected()`
- `[freedom-k66f.h:k66_automount_initialize]` Public declaration `k66_automount_initialize()`
- `[freedom-k66f.h:k66_automount_event]` Public declaration `k66_automount_event()`
- `[freedom-k66f.h:k66_pwm_setup]` Public declaration `k66_pwm_setup()`
- `[freedom-k66f.h:HAVE_PROC]` Hardware/board configuration macros (`HAVE_PROC`, `HAVE_MMCSD`, `HAVE_AUTOMOUNTER`, `HAVE_SPI`, `HAVE_USBDEV`, `HAVE_LEDS` (+17 more))
- `[k66_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[k66_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[k66_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[k66_automount.c:k66_automount_initialize]` Public function `k66_automount_initialize()`
- `[k66_automount.c:k66_automount_event]` Public function `k66_automount_event()`
- `[k66_boot.c:kinetis_boardinitialize]` Public function `kinetis_boardinitialize()`
- `[k66_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[k66_bringup.c:k66_bringup]` Public function `k66_bringup()`
- `[k66_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[k66_buttons.c:board_buttons]` Public function `board_buttons()`
- `[k66_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[k66_pwm.c:k66_pwm_setup]` Public function `k66_pwm_setup()`
- *(+20 additional symbols across 15 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_BOARDCTL_RESET`, `CONFIG_BOARDCTL_UNIQUEID`, `CONFIG_FS_AUTOMOUNTER`, `CONFIG_KINETIS_RTC` (+4 more)
- `[freedom-k66f.h:#error]` Compile-time guard: `Only one MMC/SD slot, slot 0`
- `[freedom-k66f.h:#error]` Compile-time guard: `CONFIG_KINETIS_GPIOIRQ required for card detect interrupt`
- `[k66_automount.c:DEBUGASSERT]` Requires `config != NULL && config->state != NULL`
- `[k66_bringup.c:k66_bringup]` Validates preconditions and returns `-ENODEV` on failure
- `[k66_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[k66_pwm.c:k66_pwm_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[k66_rtc.c:k66_rtc_initialize]` Validates preconditions and returns `-EIO` on failure
- `[k66_sdhc.c:k66_sdhc_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[k66_uid.c:board_uniqueid]` Validates preconditions and returns `-EINVAL` on failure
- `[k66_usbmsc.c:#error]` Compile-time guard: `Unrecognized Kinetis board`

## Side Effects
- `[k66_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[k66_automount.c:k66_automount_initialize]` Initializes/registers kernel devices or filesystems (`automount_initialize()`)
- `[k66_automount.c:k66_automount_initialize]` Modifies interrupt controller or critical-section state
- `[k66_boot.c:kinetis_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `k66_spidev_initialize()`)
- `[k66_bringup.c:k66_bringup]` Initializes/registers kernel devices or filesystems (`btn_lower_initialize()`, `k66_automount_initialize()`, `k66_rtc_initialize()`, `k66_sdhc_initialize()`, `kinetis_spibus_initialize()`)
- `[k66_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[k66_pwm.c:k66_pwm_setup]` Initializes/registers kernel devices or filesystems (`pwm_register()`)
- `[k66_rtc.c:k66_rtc_initialize]` Initializes/registers kernel devices or filesystems (`rtc_initialize()`)
- `[k66_sdhc.c:k66_sdhc_initialize]` Configures or drives hardware GPIO pins
- `[k66_sdhc.c:k66_sdhc_initialize]` Initializes/registers kernel devices or filesystems (`sdhc_initialize()`)
- `[k66_spi.c:k66_spidev_initialize]` Configures or drives hardware GPIO pins
- `[k66_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh freedom-k66f:nsh && make`
