# `twr-k64f120m/src` Component (`boards/arm/kinetis/twr-k64f120m/src`)

## Overview
Board-level C implementation (`src`) for `twr-k64f120m` (`arm/kinetis`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[twrk64.h:k64_spidev_initialize]` Public declaration `k64_spidev_initialize()`
- `[twrk64.h:k64_usbinitialize]` Public declaration `k64_usbinitialize()`
- `[twrk64.h:k64_bringup]` Public declaration `k64_bringup()`
- `[twrk64.h:k64_sdhc_initialize]` Public declaration `k64_sdhc_initialize()`
- `[twrk64.h:k64_cardinserted]` Public declaration `k64_cardinserted()`
- `[twrk64.h:k64_writeprotected]` Public declaration `k64_writeprotected()`
- `[twrk64.h:k64_automount_initialize]` Public declaration `k64_automount_initialize()`
- `[twrk64.h:k64_automount_event]` Public declaration `k64_automount_event()`
- `[twrk64.h:k64_pwm_setup]` Public declaration `k64_pwm_setup()`
- `[twrk64.h:HAVE_PROC]` Hardware/board configuration macros (`HAVE_PROC`, `HAVE_MMCSD`, `HAVE_AUTOMOUNTER`, `HAVE_USBDEV`, `HAVE_RTC_DRIVER`, `PROCFS_MOUNTPOUNT` (+28 more))
- `[k64_automount.c:k64_automount_initialize]` Public function `k64_automount_initialize()`
- `[k64_automount.c:k64_automount_event]` Public function `k64_automount_event()`
- `[k64_boot.c:kinetis_boardinitialize]` Public function `kinetis_boardinitialize()`
- `[k64_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[k64_leds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[k64_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[k64_leds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[k64_sdhc.c:k64_sdhc_initialize]` Public function `k64_sdhc_initialize()`
- `[k64_sdhc.c:k64_cardinserted]` Public function `k64_cardinserted()`
- `[k64_sdhc.c:k64_writeprotected]` Public function `k64_writeprotected()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_FS_AUTOMOUNTER`, `CONFIG_KINETIS_SDHC`, `CONFIG_USBDEV`, `CONFIG_USBMSC`
- `[twrk64.h:#error]` Compile-time guard: `Only one MMC/SD slot, slot 0`
- `[twrk64.h:#error]` Compile-time guard: `CONFIG_KINETIS_GPIOIRQ required for card detect interrupt`
- `[k64_automount.c:DEBUGASSERT]` Requires `config != NULL && config->state != NULL`
- `[k64_sdhc.c:k64_sdhc_initialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[k64_automount.c:k64_automount_initialize]` Initializes/registers kernel devices or filesystems (`automount_initialize()`)
- `[k64_automount.c:k64_automount_initialize]` Modifies interrupt controller or critical-section state
- `[k64_boot.c:kinetis_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `k64_sdhc_initialize()`, `kinetis_spidev_initialize()`, `nx_mount()`)
- `[k64_leds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[k64_sdhc.c:k64_sdhc_initialize]` Configures or drives hardware GPIO pins
- `[k64_sdhc.c:k64_sdhc_initialize]` Initializes/registers kernel devices or filesystems (`k64_automount_initialize()`, `sdhc_initialize()`)

## Verification
- Run: `./tools/configure.sh twr-k64f120m:nsh && make`
