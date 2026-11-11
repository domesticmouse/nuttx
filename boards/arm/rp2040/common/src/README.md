# `common/src` Component (`boards/arm/rp2040/common/src`)

## Overview
Board-level C implementation (`src`) for `common` (`arm/rp2040`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 27 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[rp2040_ads7046.c:board_ads7046_initialize]` Public function `board_ads7046_initialize()`
- `[rp2040_bmp180.c:board_bmp180_initialize]` Public function `board_bmp180_initialize()`
- `[rp2040_bmp280.c:board_bmp280_initialize]` Public function `board_bmp280_initialize()`
- `[rp2040_boot_image.c:board_boot_image]` Public function `board_boot_image()`
- `[rp2040_common_bringup.c:rp2040_common_bringup]` Public function `rp2040_common_bringup()`
- `[rp2040_common_initialize.c:rp2040_common_earlyinitialize]` Public function `rp2040_common_earlyinitialize()`
- `[rp2040_common_initialize.c:rp2040_common_initialize]` Public function `rp2040_common_initialize()`
- `[rp2040_composite.c:board_composite_initialize]` Public function `board_composite_initialize()`
- `[rp2040_composite.c:board_composite_connect]` Public function `board_composite_connect()`
- `[rp2040_enc28j60.c:arm_netinitialize]` Public function `arm_netinitialize()`
- `[rp2040_firmware.c:g_cyw43439_nvram_len]` Exported global symbol `g_cyw43439_nvram_len`
- `[rp2040_firmware.c:g_cyw43439_firmware_len]` Exported global symbol `g_cyw43439_firmware_len`
- `[rp2040_gc9a01.c:board_lcd_initialize]` Public function `board_lcd_initialize()`
- `[rp2040_gc9a01.c:board_lcd_getdev]` Public function `board_lcd_getdev()`
- `[rp2040_gc9a01.c:board_lcd_uninitialize]` Public function `board_lcd_uninitialize()`
- `[rp2040_i2cdev.c:board_i2cdev_initialize]` Public function `board_i2cdev_initialize()`
- `[rp2040_i2sdev.c:board_i2sdev_initialize]` Public function `board_i2sdev_initialize()`
- `[rp2040_ina219.c:board_ina219_initialize]` Public function `board_ina219_initialize()`
- `[rp2040_lcd_backpack.c:board_lcd_backpack_init]` Public function `board_lcd_backpack_init()`
- `[rp2040_max6675.c:board_max6675_initialize]` Public function `board_max6675_initialize()`
- `[rp2040_pwmdev.c:path]` Module symbol `path`
- `[rp2040_reset.c:board_reset]` Public function `board_reset()`
- `[rp2040_spi.c:rp2040_spi0select]` Public function `rp2040_spi0select()`
- *(+26 additional symbols across 27 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ADC_ADS7046`, `CONFIG_ARCH`, `CONFIG_ARCH_BOARD_COMMON`, `CONFIG_BOARDCTL_BOOT_IMAGE`, `CONFIG_BOARDCTL_RESET`, `CONFIG_BOARDCTL_UNIQUEID` (+22 more)
- `[rp2040_ads7046.c:board_ads7046_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[rp2040_bmp180.c:board_bmp180_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[rp2040_bmp280.c:board_bmp280_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[rp2040_composite.c:DEBUGASSERT]` Requires `g_mschandle == NULL`
- `[rp2040_enc28j60.c:#error]` Compile-time guard: `Need CONFIG_RP2040_ENC28J60_INTR_GPIO to specify the interrupt pin`
- `[rp2040_gc9a01.c:#error]` Compile-time guard: `The GC9A01 driver requires CONFIG_SPI_CMDATA in the config`
- `[rp2040_i2cdev.c:board_i2cdev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[rp2040_i2sdev.c:board_i2sdev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[rp2040_ina219.c:board_ina219_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[rp2040_lcd_backpack.c:board_lcd_backpack_init]` Validates preconditions and returns `-ENODEV` on failure
- `[rp2040_max6675.c:board_max6675_initialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[rp2040_ads7046.c:board_ads7046_initialize]` Initializes/registers kernel devices or filesystems (`ads7046_register()`)
- `[rp2040_bmp180.c:board_bmp180_initialize]` Initializes/registers kernel devices or filesystems (`bmp180_register()`, `rp2040_i2cbus_initialize()`)
- `[rp2040_bmp280.c:board_bmp280_initialize]` Initializes/registers kernel devices or filesystems (`bmp280_register()`, `rp2040_i2cbus_initialize()`)
- `[rp2040_boot_image.c:board_boot_image]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[rp2040_common_bringup.c:rp2040_common_bringup]` Initializes/registers kernel devices or filesystems (`adc_register()`, `board_ads7046_initialize()`, `board_bmp180_initialize()`, `board_bmp280_initialize()`, `board_i2cdev_initialize()`)
- `[rp2040_common_initialize.c:rp2040_common_earlyinitialize]` Initializes/registers kernel devices or filesystems (`rp2040_gpio_initialize()`, `rp2040_uniqueid_initialize()`)
- `[rp2040_composite.c:board_composite_initialize]` Initializes/registers kernel devices or filesystems (`composite_initialize()`)
- `[rp2040_enc28j60.c:arm_netinitialize]` Initializes/registers kernel devices or filesystems (`enc_initialize()`, `rp2040_spibus_initialize()`)
- `[rp2040_gc9a01.c:board_lcd_initialize]` Initializes/registers kernel devices or filesystems (`rp2040_spibus_initialize()`)
- `[rp2040_i2cdev.c:board_i2cdev_initialize]` Initializes/registers kernel devices or filesystems (`i2c_register()`, `rp2040_i2cbus_initialize()`)
- `[rp2040_i2sdev.c:board_i2sdev_initialize]` Initializes/registers kernel devices or filesystems (`audio_i2s_initialize()`, `audio_register()`, `i2schar_register()`, `pcm_decode_initialize()`, `rp2040_i2sbus_initialize()`)
- `[rp2040_ina219.c:board_ina219_initialize]` Initializes/registers kernel devices or filesystems (`ina219_register()`, `rp2040_i2cbus_initialize()`)

## Verification
- Run: `./tools/configure.sh sim:nsh && make`
