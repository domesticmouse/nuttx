# `freedom-k64f/src` Component (`boards/arm/kinetis/freedom-k64f/src`)

## Overview
Board-level C implementation (`src`) for `freedom-k64f` (`arm/kinetis`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 14 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[freedom-k64f.h:k64_i2cdev_initialize]` Public declaration `k64_i2cdev_initialize()`
- `[freedom-k64f.h:k64_spidev_initialize]` Public declaration `k64_spidev_initialize()`
- `[freedom-k64f.h:k64_usbinitialize]` Public declaration `k64_usbinitialize()`
- `[freedom-k64f.h:k64_bringup]` Public declaration `k64_bringup()`
- `[freedom-k64f.h:k64_sdhc_initialize]` Public declaration `k64_sdhc_initialize()`
- `[freedom-k64f.h:k64_cardinserted]` Public declaration `k64_cardinserted()`
- `[freedom-k64f.h:k64_writeprotected]` Public declaration `k64_writeprotected()`
- `[freedom-k64f.h:k64_automount_initialize]` Public declaration `k64_automount_initialize()`
- `[freedom-k64f.h:k64_automount_event]` Public declaration `k64_automount_event()`
- `[freedom-k64f.h:k64_pwm_setup]` Public declaration `k64_pwm_setup()`
- `[freedom-k64f.h:HAVE_PROC]` Hardware/board configuration macros (`HAVE_PROC`, `HAVE_MMCSD`, `HAVE_AUTOMOUNTER`, `HAVE_USBDEV`, `HAVE_LEDS`, `HAVE_RTC_DRIVER` (+15 more))
- `[k64_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[k64_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[k64_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[k64_automount.c:k64_automount_initialize]` Public function `k64_automount_initialize()`
- `[k64_automount.c:k64_automount_event]` Public function `k64_automount_event()`
- `[k64_boot.c:kinetis_boardinitialize]` Public function `kinetis_boardinitialize()`
- `[k64_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[k64_bringup.c:k64_bringup]` Public function `k64_bringup()`
- `[k64_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[k64_buttons.c:board_buttons]` Public function `board_buttons()`
- `[k64_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[k64_i2c.c:k64_i2cdev_initialize]` Public function `k64_i2cdev_initialize()`
- *(+19 additional symbols across 14 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_BOARDCTL_UNIQUEID`, `CONFIG_FS_AUTOMOUNTER`, `CONFIG_I2C`, `CONFIG_KINETIS_SDHC` (+3 more)
- `[freedom-k64f.h:#error]` Compile-time guard: `Only one MMC/SD slot, slot 0`
- `[freedom-k64f.h:#error]` Compile-time guard: `CONFIG_KINETIS_GPIOIRQ required for card detect interrupt`
- `[k64_automount.c:DEBUGASSERT]` Requires `config != NULL && config->state != NULL`
- `[k64_bringup.c:k64_bringup]` Validates preconditions and returns `-ENODEV` on failure
- `[k64_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[k64_i2c.c:k64_i2cdev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[k64_pwm.c:k64_pwm_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[k64_sdhc.c:k64_sdhc_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[k64_uid.c:board_uniqueid]` Validates preconditions and returns `-EINVAL` on failure
- `[k64_usbmsc.c:#error]` Compile-time guard: `Unrecognized Kinetis board`

## Side Effects
- `[k64_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[k64_automount.c:k64_automount_initialize]` Initializes/registers kernel devices or filesystems (`automount_initialize()`)
- `[k64_automount.c:k64_automount_initialize]` Modifies interrupt controller or critical-section state
- `[k64_boot.c:kinetis_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `k64_spidev_initialize()`)
- `[k64_bringup.c:k64_bringup]` Initializes/registers kernel devices or filesystems (`k64_automount_initialize()`, `k64_i2cdev_initialize()`, `k64_sdhc_initialize()`, `kinetis_spibus_initialize()`, `nx_mount()`)
- `[k64_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[k64_i2c.c:k64_i2cdev_initialize]` Initializes/registers kernel devices or filesystems (`fxos8700cq_register()`, `i2c_register()`, `kinetis_i2cbus_initialize()`)
- `[k64_pwm.c:k64_pwm_setup]` Initializes/registers kernel devices or filesystems (`pwm_register()`)
- `[k64_sdhc.c:k64_sdhc_initialize]` Configures or drives hardware GPIO pins
- `[k64_sdhc.c:k64_sdhc_initialize]` Initializes/registers kernel devices or filesystems (`sdhc_initialize()`)
- `[k64_spi.c:k64_spidev_initialize]` Configures or drives hardware GPIO pins
- `[k64_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh freedom-k64f:nsh && make`
