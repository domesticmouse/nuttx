# `common/src` Component (`boards/risc-v/mpfs/common/src`)

## Overview
Board-level C implementation (`src`) for `common` (`risc-v/mpfs`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[mpfs_board_spi.c:mpfs_board_spi_init]` Public function `mpfs_board_spi_init()`
- `[mpfs_boot.c:mpfs_boardinitialize]` Public function `mpfs_boardinitialize()`
- `[mpfs_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[mpfs_composite.c:board_composite_initialize]` Public function `board_composite_initialize()`
- `[mpfs_composite.c:board_composite_uninitialize]` Public function `board_composite_uninitialize()`
- `[mpfs_composite.c:board_usbmsc_initialize]` Public function `board_usbmsc_initialize()`
- `[mpfs_composite.c:board_composite_connect]` Public function `board_composite_connect()`
- `[mpfs_emmcsd.c:mpfs_board_register_partition]` Public function `mpfs_board_register_partition()`
- `[mpfs_emmcsd.c:mpfs_board_emmcsd_init]` Public function `mpfs_board_emmcsd_init()`
- `[mpfs_i2c.c:mpfs_board_i2c_init]` Public function `mpfs_board_i2c_init()`
- `[mpfs_ihc.c:mpfs_board_ihc_init]` Public function `mpfs_board_ihc_init()`
- `[mpfs_pwm.c:mpfs_pwm_setup]` Public function `mpfs_pwm_setup()`
- `[mpfs_usb.c:mpfs_board_usb_init]` Public function `mpfs_board_usb_init()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BOARD_COMMON`, `CONFIG_I2C`, `CONFIG_MPFS_EMMCSD`, `CONFIG_MPFS_HAVE_COREPWM`, `CONFIG_MPFS_IHC_CLIENT` (+3 more)
- `[mpfs_board_spi.c:mpfs_board_spi_init]` Validates preconditions and returns `-ENODEV` on failure
- `[mpfs_composite.c:DEBUGASSERT]` Requires `g_mschandle == NULL`
- `[mpfs_emmcsd.c:mpfs_board_register_partition]` Validates preconditions and returns `-ENODEV` on failure
- `[mpfs_i2c.c:mpfs_board_i2c_init]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[mpfs_board_spi.c:mpfs_board_spi_init]` Initializes/registers kernel devices or filesystems (`mpfs_corespibus_initialize()`, `mpfs_spibus_initialize()`, `spi_register()`)
- `[mpfs_boot.c:mpfs_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[mpfs_composite.c:board_composite_initialize]` Initializes/registers kernel devices or filesystems (`composite_initialize()`)
- `[mpfs_emmcsd.c:mpfs_board_register_partition]` Configures or drives hardware GPIO pins
- `[mpfs_emmcsd.c:mpfs_board_register_partition]` Initializes/registers kernel devices or filesystems (`sdio_initialize()`)
- `[mpfs_i2c.c:mpfs_board_i2c_init]` Initializes/registers kernel devices or filesystems (`i2c_register()`, `mpfs_i2cbus_initialize()`)
- `[mpfs_pwm.c:mpfs_pwm_setup]` Initializes/registers kernel devices or filesystems (`pwm_register()`)
- `[mpfs_usb.c:mpfs_board_usb_init]` Initializes/registers kernel devices or filesystems (`board_composite_initialize()`, `cdcacm_initialize()`)

## Verification
- Run: `./tools/configure.sh sim:nsh && make`
