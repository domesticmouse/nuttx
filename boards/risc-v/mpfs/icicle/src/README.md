# `icicle/src` Component (`boards/risc-v/mpfs/icicle/src`)

## Overview
Board-level C implementation (`src`) for `icicle` (`risc-v/mpfs`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 3 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[board_config.h:mpfs_bringup]` Public declaration `mpfs_bringup()`
- `[board_config.h:mpfs_board_spi_init]` Public declaration `mpfs_board_spi_init()`
- `[board_config.h:mpfs_board_i2c_init]` Public declaration `mpfs_board_i2c_init()`
- `[board_config.h:mpfs_board_ihc_init]` Public declaration `mpfs_board_ihc_init()`
- `[board_config.h:mpfs_board_emmcsd_init]` Public declaration `mpfs_board_emmcsd_init()`
- `[board_config.h:mpfs_board_usb_init]` Public declaration `mpfs_board_usb_init()`
- `[board_config.h:mpfs_pwm_setup]` Public declaration `mpfs_pwm_setup()`
- `[board_config.h:SDIO_SLOTNO]` Hardware/board configuration macros (`SDIO_SLOTNO`, `SDIO_MINOR`, `ICICLE_GPIO_LED1`, `ICICLE_GPIO_LED2`, `ICICLE_GPIO_LED3`, `ICICLE_GPIO_LED4` (+4 more))
- `[mpfs_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[mpfs_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[mpfs_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[mpfs_bringup.c:mpfs_bringup]` Public function `mpfs_bringup()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_LEDS`

## Side Effects
- `[mpfs_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[mpfs_bringup.c:mpfs_bringup]` Initializes/registers kernel devices or filesystems (`romdisk_register()`)

## Verification
- Run: `./tools/configure.sh icicle:nsh && make`
