# `drivers/sensors` Component (`boards/arm/cxd56xx/drivers/sensors`)

## Overview
Board support component `sensors` for `drivers` (`arm/cxd56xx`), containing 12 source/script file(s) (`ak09912_scu.c, apds9930_scu.c, bh1721fvc_scu.c, bh1745nuc_scu.c`).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[Kconfig:SCU_SENSORS]` Kconfig symbols (`CONFIG_SCU_SENSORS`, `CONFIG_SENSORS_AK09912_SCU`, `CONFIG_SENSORS_AK09912_SCU_DECI`, `CONFIG_SENSORS_APDS9930_SCU`, `CONFIG_SENSORS_APDS9930_PROXIMITY_INTERRUPT`, `CONFIG_SENSORS_BH1721FVC_SCU` (+21 more))
- `[ak09912_scu.c:ak09912_init]` Public function `ak09912_init()`
- `[ak09912_scu.c:ak09912_scu_register]` Public function `ak09912_scu_register()`
- `[apds9930_scu.c:apds9930_init]` Public function `apds9930_init()`
- `[apds9930_scu.c:apds9930als_register]` Public function `apds9930als_register()`
- `[apds9930_scu.c:apds9930ps_register]` Public function `apds9930ps_register()`
- `[bh1721fvc_scu.c:bh1721fvc_init]` Public function `bh1721fvc_init()`
- `[bh1721fvc_scu.c:bh1721fvc_register]` Public function `bh1721fvc_register()`
- `[bh1745nuc_scu.c:bh1745nuc_init]` Public function `bh1745nuc_init()`
- `[bh1745nuc_scu.c:bh1745nuc_register]` Public function `bh1745nuc_register()`
- `[bm1383glv_scu.c:bm1383glv_init]` Public function `bm1383glv_init()`
- `[bm1383glv_scu.c:bm1383glv_register]` Public function `bm1383glv_register()`
- `[bm1422gmv_scu.c:bm1422gmv_init]` Public function `bm1422gmv_init()`
- `[bm1422gmv_scu.c:bm1422gmv_register]` Public function `bm1422gmv_register()`
- `[bmi160_scu.c:g_bmi160gyrofops]` Module symbol `g_bmi160gyrofops`
- `[bmp280_scu.c:bmp280_init]` Public function `bmp280_init()`
- `[bmp280_scu.c:bmp280press_register]` Public function `bmp280press_register()`
- `[bmp280_scu.c:bmp280temp_register]` Public function `bmp280temp_register()`
- `[cxd5610_gnss.c:cxd5610_gnss_register]` Public function `cxd5610_gnss_register()`
- `[kx022_scu.c:kx022_init]` Public function `kx022_init()`
- `[kx022_scu.c:kx022_register]` Public function `kx022_register()`
- `[lt1pa01_scu.c:lt1pa01_init]` Public function `lt1pa01_init()`
- `[lt1pa01_scu.c:lt1pa01als_register]` Public function `lt1pa01als_register()`
- *(+4 additional symbols across 12 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_SENSORS_AK09912_SCU`, `CONFIG_SENSORS_APDS9930_SCU`, `CONFIG_SENSORS_BH1721FVC_SCU`, `CONFIG_SENSORS_BH1745NUC_SCU`, `CONFIG_SENSORS_BM1383GLV_SCU`, `CONFIG_SENSORS_BM1422GMV_SCU` (+6 more)
- `[ak09912_scu.c:DEBUGASSERT]` Requires `g_seq == NULL`
- `[ak09912_scu.c:DEBUGASSERT]` Requires `g_seq`
- `[apds9930_scu.c:DEBUGASSERT]` Requires `g_als_seq == NULL`
- `[apds9930_scu.c:DEBUGASSERT]` Requires `g_ps_seq == NULL`
- `[bh1721fvc_scu.c:DEBUGASSERT]` Requires `g_seq == NULL`
- `[bh1745nuc_scu.c:DEBUGASSERT]` Requires `g_seq == NULL`
- `[bm1383glv_scu.c:DEBUGASSERT]` Requires `g_seq == NULL`
- `[bm1422gmv_scu.c:DEBUGASSERT]` Requires `g_seq == NULL`
- `[bmi160_scu.c:DEBUGASSERT]` Requires `!g_seq_gyro`
- `[bmi160_scu.c:DEBUGASSERT]` Requires `!g_seq_accel`
- `[bmi160_scu.c:DEBUGASSERT]` Requires `g_seq_gyro`

## Side Effects
- `[ak09912_scu.c:ak09912_init]` Initializes/registers kernel devices or filesystems (`register_driver()`)
- `[apds9930_scu.c:apds9930_init]` Initializes/registers kernel devices or filesystems (`register_driver()`)
- `[apds9930_scu.c:apds9930_init]` Modifies interrupt controller or critical-section state
- `[bh1721fvc_scu.c:bh1721fvc_init]` Initializes/registers kernel devices or filesystems (`register_driver()`)
- `[bh1745nuc_scu.c:bh1745nuc_init]` Initializes/registers kernel devices or filesystems (`register_driver()`)
- `[bm1383glv_scu.c:bm1383glv_init]` Initializes/registers kernel devices or filesystems (`register_driver()`)
- `[bm1422gmv_scu.c:bm1422gmv_init]` Initializes/registers kernel devices or filesystems (`register_driver()`)
- `[bmi160_scu.c:g_bmi160gyrofops]` Initializes/registers kernel devices or filesystems (`bmi160accel_register()`, `bmi160gyro_register()`, `register_driver()`)
- `[bmp280_scu.c:bmp280_init]` Initializes/registers kernel devices or filesystems (`bmp280_initialize()`, `register_driver()`)
- `[cxd5610_gnss.c:cxd5610_gnss_register]` Initializes/registers kernel devices or filesystems (`cxd5610_gnss_core_initialize()`, `cxd5610_gnss_initialize()`, `register_driver()`)
- `[kx022_scu.c:kx022_init]` Initializes/registers kernel devices or filesystems (`kx022_initialize()`, `register_driver()`)
- `[lt1pa01_scu.c:lt1pa01_init]` Initializes/registers kernel devices or filesystems (`register_driver()`)

## Verification
- Run: `./tools/configure.sh sim:nsh && make`
