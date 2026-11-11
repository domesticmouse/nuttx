# `common/src` Component (`boards/arm/nrf53/common/src`)

## Overview
Board-level C implementation (`src`) for `common` (`arm/nrf53`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 10 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[nrf53_adxl362.c:nrf53_adxl362_init]` Public function `nrf53_adxl362_init()`
- `[nrf53_bh1749nuc.c:nrf53_bh1749nuc_init]` Public function `nrf53_bh1749nuc_init()`
- `[nrf53_bme688.c:nrf53_bme688_init]` Public function `nrf53_bme688_init()`
- `[nrf53_bmi270.c:nrf53_bmi270spi_initialize]` Public function `nrf53_bmi270spi_initialize()`
- `[nrf53_bmi270.c:nrf53_bmi270i2c_initialize]` Public function `nrf53_bmi270i2c_initialize()`
- `[nrf53_bmm150.c:nrf53_bmm150_init]` Public function `nrf53_bmm150_init()`
- `[nrf53_boot_image.c:board_boot_image]` Public function `board_boot_image()`
- `[nrf53_ieee802154.c:nrf53_ieee802154_initialize]` Public function `nrf53_ieee802154_initialize()`
- `[nrf53_progmem.c:nrf53_progmem_init]` Public function `nrf53_progmem_init()`
- `[nrf53_reset.c:board_reset]` Public function `board_reset()`
- `[nrf53_timer.c:nrf53_timer_driver_setup]` Public function `nrf53_timer_driver_setup()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BOARD_COMMON`, `CONFIG_BOARDCTL_BOOT_IMAGE`, `CONFIG_BOARDCTL_RESET`, `CONFIG_NRF53_PROGMEM`, `CONFIG_NRF53_RADIO_IEEE802154` (+6 more)
- `[nrf53_adxl362.c:nrf53_adxl362_init]` Validates preconditions and returns `-ENODEV` on failure
- `[nrf53_bh1749nuc.c:#error]` Compile-time guard: `BH1749NUC UORB is only supported`
- `[nrf53_bme688.c:nrf53_bme688_init]` Validates preconditions and returns `-ENODEV` on failure
- `[nrf53_bmi270.c:nrf53_bmi270spi_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[nrf53_bmm150.c:nrf53_bmm150_init]` Validates preconditions and returns `-ENODEV` on failure
- `[nrf53_ieee802154.c:nrf53_ieee802154_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[nrf53_progmem.c:ASSERT]` Requires `(mtd_offset % up_progmem_pagesize(0)) == 0`
- `[nrf53_progmem.c:ASSERT]` Requires `(mtd_size % up_progmem_pagesize(0)) == 0`
- `[nrf53_progmem.c:#error]` Compile-time guard: `CONFIG_MTD_PARTITION is required`

## Side Effects
- `[nrf53_adxl362.c:nrf53_adxl362_init]` Initializes/registers kernel devices or filesystems (`adxl362_register()`, `nrf53_spibus_initialize()`)
- `[nrf53_bh1749nuc.c:nrf53_bh1749nuc_init]` Initializes/registers kernel devices or filesystems (`nrf53_i2cbus_initialize()`)
- `[nrf53_bme688.c:nrf53_bme688_init]` Initializes/registers kernel devices or filesystems (`bme688_register()`, `nrf53_i2cbus_initialize()`)
- `[nrf53_bmi270.c:nrf53_bmi270spi_initialize]` Initializes/registers kernel devices or filesystems (`nrf53_i2cbus_initialize()`, `nrf53_spibus_initialize()`)
- `[nrf53_bmm150.c:nrf53_bmm150_init]` Initializes/registers kernel devices or filesystems (`nrf53_i2cbus_initialize()`)
- `[nrf53_boot_image.c:board_boot_image]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[nrf53_ieee802154.c:nrf53_ieee802154_initialize]` Initializes/registers kernel devices or filesystems (`mac802154dev_register()`, `mac802154netdev_register()`, `nrf53_radioi8_register()`)
- `[nrf53_progmem.c:nrf53_progmem_init]` Initializes/registers kernel devices or filesystems (`progmem_initialize()`)
- `[nrf53_timer.c:nrf53_timer_driver_setup]` Initializes/registers kernel devices or filesystems (`nrf53_timer_initialize()`)

## Verification
- Run: `./tools/configure.sh sim:nsh && make`
