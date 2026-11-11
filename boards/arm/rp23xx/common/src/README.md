# `common/src` Component (`boards/arm/rp23xx/common/src`)

## Overview
Board-level C implementation (`src`) for `common` (`arm/rp23xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 16 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[rp23xx_boardctl.c:board_ioctl]` Public function `board_ioctl()`
- `[rp23xx_common_bringup.c:rp23xx_common_bringup]` Public function `rp23xx_common_bringup()`
- `[rp23xx_common_initialize.c:rp23xx_common_earlyinitialize]` Public function `rp23xx_common_earlyinitialize()`
- `[rp23xx_common_initialize.c:rp23xx_common_initialize]` Public function `rp23xx_common_initialize()`
- `[rp23xx_composite.c:board_composite_initialize]` Public function `board_composite_initialize()`
- `[rp23xx_composite.c:board_composite_connect]` Public function `board_composite_connect()`
- `[rp23xx_cyw43439_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[rp23xx_cyw43439_userleds.c:board_userled]` Public function `board_userled()`
- `[rp23xx_cyw43439_userleds.c:board_userled_all]` Public function `board_userled_all()`
- `[rp23xx_firmware.c:g_cyw43439_nvram_len]` Exported global symbol `g_cyw43439_nvram_len`
- `[rp23xx_firmware.c:g_cyw43439_firmware_len]` Exported global symbol `g_cyw43439_firmware_len`
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
- *(+8 additional symbols across 16 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BOARD_COMMON`, `CONFIG_BOARDCTL_IOCTL`, `CONFIG_BOARDCTL_RESET`, `CONFIG_BOARDCTL_UNIQUEID`, `CONFIG_CYW43439_FIRMWARE_BIN_PATH` (+20 more)
- `[rp23xx_boardctl.c:board_ioctl]` Validates preconditions and returns `-EINVAL`, `-ENOTTY` on failure
- `[rp23xx_composite.c:DEBUGASSERT]` Requires `g_mschandle == NULL`
- `[rp23xx_i2cdev.c:board_i2cdev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[rp23xx_i2sdev.c:board_i2sdev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[rp23xx_pwmdev.c:path]` Validates preconditions and returns `-ENODEV` on failure
- `[rp23xx_spi.c:rp23xx_spi0select]` Validates preconditions and returns `-ENODEV` on failure
- `[rp23xx_spidev.c:board_spidev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[rp23xx_spisd.c:board_spisd_initialize]` Validates preconditions and returns `-EINVAL`, `-ENODEV` on failure
- `[rp23xx_st7735.c:board_lcd_initialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[rp23xx_common_bringup.c:rp23xx_common_bringup]` Initializes/registers kernel devices or filesystems (`board_i2cdev_initialize()`, `board_i2sdev_initialize()`, `board_spidev_initialize()`, `board_spisd_initialize()`, `nx_mount()`)
- `[rp23xx_common_initialize.c:rp23xx_common_earlyinitialize]` Initializes/registers kernel devices or filesystems (`rp23xx_gpio_initialize()`, `rp23xx_uniqueid_initialize()`)
- `[rp23xx_composite.c:board_composite_initialize]` Initializes/registers kernel devices or filesystems (`composite_initialize()`)
- `[rp23xx_i2cdev.c:board_i2cdev_initialize]` Initializes/registers kernel devices or filesystems (`i2c_register()`, `rp23xx_i2cbus_initialize()`)
- `[rp23xx_i2sdev.c:board_i2sdev_initialize]` Initializes/registers kernel devices or filesystems (`audio_i2s_initialize()`, `audio_register()`, `i2schar_register()`, `pcm_decode_initialize()`, `rp23xx_i2sbus_initialize()`)
- `[rp23xx_pwmdev.c:path]` Initializes/registers kernel devices or filesystems (`pwm_register()`, `rp23xx_pwm_initialize()`, `rp23xx_pwmdev_initialize()`)
- `[rp23xx_spidev.c:board_spidev_initialize]` Initializes/registers kernel devices or filesystems (`rp23xx_spibus_initialize()`, `spi_register()`)
- `[rp23xx_spisd.c:board_spisd_initialize]` Initializes/registers kernel devices or filesystems (`nx_mount()`, `rp23xx_spibus_initialize()`)
- `[rp23xx_st7735.c:board_lcd_initialize]` Initializes/registers kernel devices or filesystems (`rp23xx_spibus_initialize()`)

## Verification
- Run: `./tools/configure.sh sim:nsh && make`
