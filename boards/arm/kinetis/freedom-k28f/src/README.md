# `freedom-k28f/src` Component (`boards/arm/kinetis/freedom-k28f/src`)

## Overview
Board-level C implementation (`src`) for `freedom-k28f` (`arm/kinetis`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 12 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[freedom-k28f.h:k28_bringup]` Public declaration `k28_bringup()`
- `[freedom-k28f.h:k28_spidev_initialize]` Public declaration `k28_spidev_initialize()`
- `[freedom-k28f.h:k28_i2cdev_initialize]` Public declaration `k28_i2cdev_initialize()`
- `[freedom-k28f.h:k28_usbdev_initialize]` Public declaration `k28_usbdev_initialize()`
- `[freedom-k28f.h:k28_usbhost_initialize]` Public declaration `k28_usbhost_initialize()`
- `[freedom-k28f.h:k28_sdhc_initialize]` Public declaration `k28_sdhc_initialize()`
- `[freedom-k28f.h:k28_cardinserted]` Public declaration `k28_cardinserted()`
- `[freedom-k28f.h:k28_writeprotected]` Public declaration `k28_writeprotected()`
- `[freedom-k28f.h:k28_sdhc_automount_event]` Public declaration `k28_sdhc_automount_event()`
- `[freedom-k28f.h:k28_automount_initialize]` Public declaration `k28_automount_initialize()`
- `[freedom-k28f.h:k28_pwm_setup]` Public declaration `k28_pwm_setup()`
- `[freedom-k28f.h:HAVE_MMCSD]` Hardware/board configuration macros (`HAVE_MMCSD`, `HAVE_USB_MSC`, `HAVE_SDHC_AUTOMOUNTER`, `HAVE_USB_AUTOMOUNTER`, `MMCSD_SLOTNO`, `MMSCD_MINOR` (+16 more))
- `[k28_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[k28_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[k28_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[k28_automount.c:k28_sdhc_automount_event]` Public function `k28_sdhc_automount_event()`
- `[k28_automount.c:k28_automount_initialize]` Public function `k28_automount_initialize()`
- `[k28_boot.c:kinetis_boardinitialize]` Public function `kinetis_boardinitialize()`
- `[k28_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[k28_bringup.c:k28_bringup]` Public function `k28_bringup()`
- `[k28_i2c.c:k28_i2cdev_initialize]` Public function `k28_i2cdev_initialize()`
- `[k28_pwm.c:k28_pwm_setup]` Public function `k28_pwm_setup()`
- `[k28_sdhc.c:k28_sdhc_initialize]` Public function `k28_sdhc_initialize()`
- *(+18 additional symbols across 12 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_LEDS`, `CONFIG_FS_AUTOMOUNTER`, `CONFIG_KINETIS_SDHC`, `CONFIG_KINETIS_USBHS`, `CONFIG_KINETIS_USBOTG`, `CONFIG_PWM` (+2 more)
- `[freedom-k28f.h:#error]` Compile-time guard: `Only one MMC/SD slot, slot 0`
- `[freedom-k28f.h:#error]` Compile-time guard: `CONFIG_KINETIS_GPIOIRQ required for card detect interrupt`
- `[k28_automount.c:DEBUGASSERT]` Requires `config != NULL && config->state != NULL`
- `[k28_i2c.c:k28_i2cdev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[k28_pwm.c:k28_pwm_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[k28_sdhc.c:k28_sdhc_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[k28_usbhshost.c:k28_usbhost_initialize]` Validates preconditions and returns `-EBUSY`, `-ENODEV` on failure

## Side Effects
- `[k28_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[k28_automount.c:k28_sdhc_automount_event]` Initializes/registers kernel devices or filesystems (`automount_initialize()`)
- `[k28_automount.c:k28_sdhc_automount_event]` Modifies interrupt controller or critical-section state
- `[k28_boot.c:kinetis_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `k28_spidev_initialize()`)
- `[k28_bringup.c:k28_bringup]` Initializes/registers kernel devices or filesystems (`k28_automount_initialize()`, `k28_i2cdev_initialize()`, `k28_sdhc_initialize()`, `k28_usbdev_initialize()`, `k28_usbhost_initialize()`)
- `[k28_i2c.c:k28_i2cdev_initialize]` Initializes/registers kernel devices or filesystems (`i2c_register()`, `kinetis_i2cbus_initialize()`)
- `[k28_pwm.c:k28_pwm_setup]` Initializes/registers kernel devices or filesystems (`pwm_register()`)
- `[k28_sdhc.c:k28_sdhc_initialize]` Configures or drives hardware GPIO pins
- `[k28_sdhc.c:k28_sdhc_initialize]` Initializes/registers kernel devices or filesystems (`sdhc_initialize()`)
- `[k28_usbdev.c:k28_usbdev_initialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[k28_usbhshost.c:k28_usbhost_initialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[k28_usbhshost.c:k28_usbhost_initialize]` Initializes/registers kernel devices or filesystems (`kinetis_ehci_initialize()`, `nx_mount()`, `usbhost_cdcacm_initialize()`, `usbhost_hub_initialize()`, `usbhost_msc_initialize()`)

## Verification
- Run: `./tools/configure.sh freedom-k28f:nsh && make`
