# `common/src` Component (`boards/arm/nrf52/common/src`)

## Overview
Board-level C implementation (`src`) for `common` (`arm/nrf52`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[nrf52_boot_image.c:board_boot_image]` Public function `board_boot_image()`
- `[nrf52_ieee802154.c:nrf52_ieee802154_initialize]` Public function `nrf52_ieee802154_initialize()`
- `[nrf52_lsm9ds1.c:nrf52_lsm9ds1_initialize]` Public function `nrf52_lsm9ds1_initialize()`
- `[nrf52_mrf24j40.c:nrf52_mrf24j40_devsetup]` Public function `nrf52_mrf24j40_devsetup()`
- `[nrf52_progmem.c:nrf52_progmem_init]` Public function `nrf52_progmem_init()`
- `[nrf52_reset.c:board_reset]` Public function `board_reset()`
- `[nrf52_timer.c:nrf52_timer_driver_setup]` Public function `nrf52_timer_driver_setup()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BOARD_COMMON`, `CONFIG_BOARDCTL_BOOT_IMAGE`, `CONFIG_BOARDCTL_RESET`, `CONFIG_IEEE802154_MRF24J40`, `CONFIG_NRF52_PROGMEM` (+3 more)
- `[nrf52_ieee802154.c:nrf52_ieee802154_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[nrf52_lsm9ds1.c:nrf52_lsm9ds1_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[nrf52_mrf24j40.c:#error]` Compile-time guard: `Wireless support requires CONFIG_DRIVERS_WIRELESS`
- `[nrf52_progmem.c:ASSERT]` Requires `(mtd_offset % up_progmem_pagesize(0)) == 0`
- `[nrf52_progmem.c:ASSERT]` Requires `(mtd_size % up_progmem_pagesize(0)) == 0`
- `[nrf52_progmem.c:#error]` Compile-time guard: `CONFIG_MTD_PARTITION is required`

## Side Effects
- `[nrf52_boot_image.c:board_boot_image]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[nrf52_ieee802154.c:nrf52_ieee802154_initialize]` Initializes/registers kernel devices or filesystems (`mac802154dev_register()`, `mac802154netdev_register()`, `nrf52_radioi8_register()`)
- `[nrf52_lsm9ds1.c:nrf52_lsm9ds1_initialize]` Initializes/registers kernel devices or filesystems (`lsm9ds1accel_register()`, `lsm9ds1gyro_register()`, `lsm9ds1mag_register()`, `nrf52_i2cbus_initialize()`)
- `[nrf52_mrf24j40.c:nrf52_mrf24j40_devsetup]` Initializes/registers kernel devices or filesystems (`mac802154dev_register()`, `mac802154netdev_register()`, `nrf52_spibus_initialize()`)
- `[nrf52_progmem.c:nrf52_progmem_init]` Initializes/registers kernel devices or filesystems (`progmem_initialize()`)
- `[nrf52_timer.c:nrf52_timer_driver_setup]` Initializes/registers kernel devices or filesystems (`nrf52_timer_initialize()`)

## Verification
- Run: `./tools/configure.sh sim:nsh && make`
