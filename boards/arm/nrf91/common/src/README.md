# `common/src` Component (`boards/arm/nrf91/common/src`)

## Overview
Board-level C implementation (`src`) for `common` (`arm/nrf91`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[nrf91_adxl362.c:nrf91_adxl362_init]` Public function `nrf91_adxl362_init()`
- `[nrf91_adxl372.c:nrf91_adxl372_init]` Public function `nrf91_adxl372_init()`
- `[nrf91_bh1749nuc.c:nrf91_bh1749nuc_init]` Public function `nrf91_bh1749nuc_init()`
- `[nrf91_bme680.c:nrf91_bme680_init]` Public function `nrf91_bme680_init()`
- `[nrf91_bme680.c:g_bme680_config]` Exported global symbol `g_bme680_config`
- `[nrf91_boot_image.c:nsfunc]` Public function `nsfunc()`
- `[nrf91_boot_image.c:board_boot_image]` Public function `board_boot_image()`
- `[nrf91_progmem.c:nrf91_progmem_init]` Public function `nrf91_progmem_init()`
- `[nrf91_reset.c:board_reset]` Public function `board_reset()`
- `[nrf91_timer.c:nrf91_timer_driver_setup]` Public function `nrf91_timer_driver_setup()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BOARD_COMMON`, `CONFIG_BOARDCTL_BOOT_IMAGE`, `CONFIG_BOARDCTL_RESET`, `CONFIG_NRF91_PROGMEM`, `CONFIG_NRF91_TIMER` (+4 more)
- `[nrf91_adxl362.c:nrf91_adxl362_init]` Validates preconditions and returns `-ENODEV` on failure
- `[nrf91_adxl372.c:nrf91_adxl372_init]` Validates preconditions and returns `-ENODEV` on failure
- `[nrf91_bh1749nuc.c:#error]` Compile-time guard: `BH1749NUC UORB is only supported`
- `[nrf91_bme680.c:nrf91_bme680_init]` Validates preconditions and returns `-ENODEV` on failure
- `[nrf91_boot_image.c:#error]` Compile-time guard: `CONFIG_NRF91_OTA_PRIMARY_SLOT_OFFSET not defined`
- `[nrf91_boot_image.c:#error]` Compile-time guard: `CONFIG_NRF91_MCUBOOT_HEADER_SIZE not defined`
- `[nrf91_progmem.c:ASSERT]` Requires `(mtd_offset % up_progmem_pagesize(0)) == 0`
- `[nrf91_progmem.c:ASSERT]` Requires `(mtd_size % up_progmem_pagesize(0)) == 0`
- `[nrf91_progmem.c:#error]` Compile-time guard: `CONFIG_MTD_PARTITION is required`

## Side Effects
- `[nrf91_adxl362.c:nrf91_adxl362_init]` Initializes/registers kernel devices or filesystems (`adxl362_register()`, `nrf91_spibus_initialize()`)
- `[nrf91_adxl372.c:nrf91_adxl372_init]` Initializes/registers kernel devices or filesystems (`nrf91_spibus_initialize()`)
- `[nrf91_bh1749nuc.c:nrf91_bh1749nuc_init]` Initializes/registers kernel devices or filesystems (`nrf91_i2cbus_initialize()`)
- `[nrf91_bme680.c:nrf91_bme680_init]` Initializes/registers kernel devices or filesystems (`bme680_register()`, `nrf91_i2cbus_initialize()`)
- `[nrf91_boot_image.c:nsfunc]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[nrf91_progmem.c:nrf91_progmem_init]` Initializes/registers kernel devices or filesystems (`progmem_initialize()`)
- `[nrf91_timer.c:nrf91_timer_driver_setup]` Initializes/registers kernel devices or filesystems (`nrf91_timer_initialize()`)

## Verification
- Run: `./tools/configure.sh sim:nsh && make`
