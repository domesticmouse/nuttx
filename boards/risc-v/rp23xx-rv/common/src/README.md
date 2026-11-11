# `common/src` Component (`boards/risc-v/rp23xx-rv/common/src`)

## Overview
Board-level C implementation (`src`) for `common` (`risc-v/rp23xx-rv`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 12 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[rp23xx_common_bringup.c:rp23xx_common_bringup]` Public function `rp23xx_common_bringup()`
- `[rp23xx_common_initialize.c:rp23xx_common_earlyinitialize]` Public function `rp23xx_common_earlyinitialize()`
- `[rp23xx_common_initialize.c:rp23xx_common_initialize]` Public function `rp23xx_common_initialize()`
- `[rp23xx_composite.c:board_composite_initialize]` Public function `board_composite_initialize()`
- `[rp23xx_composite.c:board_composite_connect]` Public function `board_composite_connect()`
- `[rp23xx_i2cdev.c:board_i2cdev_initialize]` Public function `board_i2cdev_initialize()`
- `[rp23xx_i2sdev.c:board_i2sdev_initialize]` Public function `board_i2sdev_initialize()`
- `[rp23xx_pwmdev.c:path]` Module symbol `path`
- `[rp23xx_reset.c:board_reset]` Public function `board_reset()`
- `[rp23xx_spi.c:rp23xx_spi0select]` Public function `rp23xx_spi0select()`
- `[rp23xx_spi.c:rp23xx_spi0status]` Public function `rp23xx_spi0status()`
- `[rp23xx_spi.c:rp23xx_spi0cmddata]` Public function `rp23xx_spi0cmddata()`
- `[rp23xx_spi.c:rp23xx_spi1select]` Public function `rp23xx_spi1select()`
- `[rp23xx_spi.c:rp23xx_spi1status]` Public function `rp23xx_spi1status()`
- `[rp23xx_spi.c:rp23xx_spi1cmddata]` Public function `rp23xx_spi1cmddata()`
- `[rp23xx_spidev.c:board_spidev_initialize]` Public function `board_spidev_initialize()`
- `[rp23xx_spisd.c:board_spisd_initialize]` Public function `board_spisd_initialize()`
- `[rp23xx_spisd.c:board_spisd_status]` Public function `board_spisd_status()`
- `[rp23xx_uniqueid.c:int]` Public function `int()`
- `[rp23xx_uniqueid.c:rp23xx_uniqueid_initialize]` Public function `rp23xx_uniqueid_initialize()`
- `[rp23xx_uniqueid.c:board_uniqueid]` Public function `board_uniqueid()`
- `[rp23xx_usbmsc.c:board_usbmsc_initialize]` Public function `board_usbmsc_initialize()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BOARD_COMMON`, `CONFIG_BOARDCTL_RESET`, `CONFIG_BOARDCTL_UNIQUEID`, `CONFIG_ENC28J60`, `CONFIG_LCD_BACKPACK` (+16 more)
- `[rp23xx_composite.c:DEBUGASSERT]` Requires `g_mschandle == NULL`
- `[rp23xx_i2cdev.c:board_i2cdev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[rp23xx_i2sdev.c:board_i2sdev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[rp23xx_pwmdev.c:path]` Validates preconditions and returns `-ENODEV` on failure
- `[rp23xx_spi.c:rp23xx_spi0select]` Validates preconditions and returns `-ENODEV` on failure
- `[rp23xx_spidev.c:board_spidev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[rp23xx_spisd.c:board_spisd_initialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[rp23xx_common_bringup.c:rp23xx_common_bringup]` Initializes/registers kernel devices or filesystems (`board_i2cdev_initialize()`, `board_i2sdev_initialize()`, `board_spidev_initialize()`, `board_spisd_initialize()`, `nx_mount()`)
- `[rp23xx_common_initialize.c:rp23xx_common_earlyinitialize]` Initializes/registers kernel devices or filesystems (`rp23xx_gpio_initialize()`, `rp23xx_uniqueid_initialize()`)
- `[rp23xx_composite.c:board_composite_initialize]` Initializes/registers kernel devices or filesystems (`composite_initialize()`)
- `[rp23xx_i2cdev.c:board_i2cdev_initialize]` Initializes/registers kernel devices or filesystems (`i2c_register()`, `rp23xx_i2cbus_initialize()`)
- `[rp23xx_i2sdev.c:board_i2sdev_initialize]` Initializes/registers kernel devices or filesystems (`audio_i2s_initialize()`, `audio_register()`, `i2schar_register()`, `pcm_decode_initialize()`, `rp23xx_i2sbus_initialize()`)
- `[rp23xx_pwmdev.c:path]` Initializes/registers kernel devices or filesystems (`pwm_register()`, `rp23xx_pwm_initialize()`, `rp23xx_pwmdev_initialize()`)
- `[rp23xx_spidev.c:board_spidev_initialize]` Initializes/registers kernel devices or filesystems (`rp23xx_spibus_initialize()`, `spi_register()`)
- `[rp23xx_spisd.c:board_spisd_initialize]` Initializes/registers kernel devices or filesystems (`nx_mount()`, `rp23xx_spibus_initialize()`)

## Verification
- Run: `./tools/configure.sh sim:nsh && make`
