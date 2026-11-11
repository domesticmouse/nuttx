# `arty_a7/src` Component (`boards/risc-v/litex/arty_a7/src`)

## Overview
Board-level C implementation (`src`) for `arty_a7` (`risc-v/litex`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 9 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[arty_a7.h:litex_bringup]` Public declaration `litex_bringup()`
- `[arty_a7.h:litex_sdio_initialize]` Public declaration `litex_sdio_initialize()`
- `[arty_a7.h:litex_automount_initialize]` Public declaration `litex_automount_initialize()`
- `[arty_a7.h:litex_automount_event]` Public declaration `litex_automount_event()`
- `[arty_a7.h:litex_cardinserted]` Public declaration `litex_cardinserted()`
- `[arty_a7.h:litex_pwm_setup]` Public declaration `litex_pwm_setup()`
- `[arty_a7.h:litex_mount_ramdisk]` Public declaration `litex_mount_ramdisk()`
- `[arty_a7.h:HAVE_SDMMC]` Hardware/board configuration macros (`HAVE_SDMMC`, `HAVE_AUTOMOUNTER`, `SDIO_MINOR`, `SDIO_SLOTNO`, `LITEX_PROCFS_MOUNTPOINT`)
- `[litex_automount.c:litex_automount_initialize]` Public function `litex_automount_initialize()`
- `[litex_automount.c:litex_automount_event]` Public function `litex_automount_event()`
- `[litex_boardinit.c:board_late_initialize]` Public function `board_late_initialize()`
- `[litex_boot.c:litex_boardinitialize]` Public function `litex_boardinitialize()`
- `[litex_bringup.c:litex_bringup]` Public function `litex_bringup()`
- `[litex_pwm.c:litex_pwm_setup]` Public function `litex_pwm_setup()`
- `[litex_ramdisk.c:litex_mount_ramdisk]` Public function `litex_mount_ramdisk()`
- `[litex_reset.c:board_reset]` Public function `board_reset()`
- `[litex_sdio.c:litex_cardinserted]` Public function `litex_cardinserted()`
- `[litex_sdio.c:litex_sdio_initialize]` Public function `litex_sdio_initialize()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_BOARDCTL_RESET`, `CONFIG_FS_AUTOMOUNTER`, `CONFIG_LITEX_APPLICATION_RAMDISK`, `CONFIG_LITEX_PWM`, `CONFIG_LITEX_SDIO`
- `[litex_automount.c:DEBUGASSERT]` Requires `config && config->state`
- `[litex_pwm.c:litex_pwm_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[litex_ramdisk.c:#error]` Compile-time guard: `Ramdisk usage is intended to be used with kernel build only`
- `[litex_reset.c:board_reset]` Validates preconditions and returns `-ENODEV` on failure
- `[litex_sdio.c:litex_cardinserted]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[litex_automount.c:litex_automount_initialize]` Initializes/registers kernel devices or filesystems (`automount_initialize()`)
- `[litex_automount.c:litex_automount_initialize]` Modifies interrupt controller or critical-section state
- `[litex_bringup.c:litex_bringup]` Initializes/registers kernel devices or filesystems (`litex_automount_initialize()`, `litex_sdio_initialize()`, `nx_mount()`)
- `[litex_pwm.c:litex_pwm_setup]` Initializes/registers kernel devices or filesystems (`pwm_register()`)
- `[litex_sdio.c:litex_cardinserted]` Initializes/registers kernel devices or filesystems (`sdio_initialize()`)

## Verification
- Run: `./tools/configure.sh arty_a7:nsh && make`
