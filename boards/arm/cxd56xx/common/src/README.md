# `common/src` Component (`boards/arm/cxd56xx/common/src`)

## Overview
Board-level C implementation (`src`) for `common` (`arm/cxd56xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 43 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[cxd56_ak09912_i2c.c:board_ak09912_initialize]` Public function `board_ak09912_initialize()`
- `[cxd56_ak09912_scu.c:board_ak09912_initialize]` Public function `board_ak09912_initialize()`
- `[cxd56_alt1250.c:board_alt1250_initialize]` Public function `board_alt1250_initialize()`
- `[cxd56_alt1250.c:board_alt1250_reset]` Public function `board_alt1250_reset()`
- `[cxd56_apds9930_scu.c:board_apds9930_initialize]` Public function `board_apds9930_initialize()`
- `[cxd56_apds9960_i2c.c:board_apds9960_initialize]` Public function `board_apds9960_initialize()`
- `[cxd56_audio.c:board_audio_power_control]` Public function `board_audio_power_control()`
- `[cxd56_audio.c:board_aca_power_control]` Public function `board_aca_power_control()`
- `[cxd56_audio.c:board_aca_power_monitor]` Public function `board_aca_power_monitor()`
- `[cxd56_audio.c:board_external_amp_mute_control]` Public function `board_external_amp_mute_control()`
- `[cxd56_audio.c:board_external_amp_mute_monitor]` Public function `board_external_amp_mute_monitor()`
- `[cxd56_audio.c:board_audio_i2s_enable]` Public function `board_audio_i2s_enable()`
- `[cxd56_audio.c:board_audio_i2s_disable]` Public function `board_audio_i2s_disable()`
- `[cxd56_audio.c:board_audio_initialize]` Public function `board_audio_initialize()`
- `[cxd56_audio.c:board_audio_finalize]` Public function `board_audio_finalize()`
- `[cxd56_audio.c:board_audio_initialize_driver]` Public function `board_audio_initialize_driver()`
- `[cxd56_bcm20706.c:board_bluetooth_pin_cfg]` Public function `board_bluetooth_pin_cfg()`
- `[cxd56_bcm20706.c:board_bluetooth_uart_pin_cfg]` Public function `board_bluetooth_uart_pin_cfg()`
- `[cxd56_bcm20706.c:board_bluetooth_reset]` Public function `board_bluetooth_reset()`
- `[cxd56_bcm20706.c:board_bluetooth_power_control]` Public function `board_bluetooth_power_control()`
- `[cxd56_bcm20706.c:board_bluetooth_enable_sleep]` Public function `board_bluetooth_enable_sleep()`
- `[cxd56_bh1721fvc_scu.c:board_bh1721fvc_initialize]` Public function `board_bh1721fvc_initialize()`
- `[cxd56_bh1745nuc_scu.c:board_bh1745nuc_initialize]` Public function `board_bh1745nuc_initialize()`
- `[cxd56_bm1383glv_scu.c:board_bm1383glv_initialize]` Public function `board_bm1383glv_initialize()`
- *(+61 additional symbols across 43 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BOARD_COMMON`, `CONFIG_AUDIO_CXD56`, `CONFIG_BCM20706`, `CONFIG_BOARDCTL_UNIQUEID`, `CONFIG_BOARD_USBDEV_SERIALSTR` (+39 more)
- `[cxd56_ak09912_i2c.c:board_ak09912_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[cxd56_ak09912_scu.c:board_ak09912_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[cxd56_alt1250.c:#error]` Compile-time guard: `Select LTE SPI 4 or 5`
- `[cxd56_apds9930_scu.c:board_apds9930_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[cxd56_apds9960_i2c.c:board_apds9960_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[cxd56_audio.c:#error]` Compile-time guard: `CXD5247_XRST must be defined in board.h !!`
- `[cxd56_audio.c:#error]` Compile-time guard: `CXD5247_AVDD must be defined in board.h !!`
- `[cxd56_bh1721fvc_scu.c:board_bh1721fvc_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[cxd56_bh1745nuc_scu.c:board_bh1745nuc_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[cxd56_bm1383glv_scu.c:board_bm1383glv_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[cxd56_bm1422gmv_scu.c:board_bm1422gmv_initialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[cxd56_ak09912_i2c.c:board_ak09912_initialize]` Initializes/registers kernel devices or filesystems (`ak09912_register()`, `cxd56_i2cbus_initialize()`)
- `[cxd56_ak09912_scu.c:board_ak09912_initialize]` Initializes/registers kernel devices or filesystems (`ak09912_scu_register()`, `cxd56_i2cbus_initialize()`)
- `[cxd56_alt1250.c:board_alt1250_initialize]` Configures or drives hardware GPIO pins
- `[cxd56_alt1250.c:board_alt1250_initialize]` Initializes/registers kernel devices or filesystems (`alt1250_register()`, `cxd56_spibus_initialize()`)
- `[cxd56_apds9930_scu.c:board_apds9930_initialize]` Initializes/registers kernel devices or filesystems (`apds9930als_register()`, `apds9930ps_register()`, `cxd56_i2cbus_initialize()`)
- `[cxd56_apds9960_i2c.c:board_apds9960_initialize]` Initializes/registers kernel devices or filesystems (`apds9960_register()`, `cxd56_i2cbus_initialize()`)
- `[cxd56_audio.c:board_audio_power_control]` Configures or drives hardware GPIO pins
- `[cxd56_audio.c:board_audio_power_control]` Initializes/registers kernel devices or filesystems (`audio_register()`, `cxd56_initialize()`, `pcm_decode_initialize()`)
- `[cxd56_bh1721fvc_scu.c:board_bh1721fvc_initialize]` Initializes/registers kernel devices or filesystems (`bh1721fvc_register()`, `cxd56_i2cbus_initialize()`)
- `[cxd56_bh1745nuc_scu.c:board_bh1745nuc_initialize]` Initializes/registers kernel devices or filesystems (`bh1745nuc_register()`, `cxd56_i2cbus_initialize()`)
- `[cxd56_bm1383glv_scu.c:board_bm1383glv_initialize]` Initializes/registers kernel devices or filesystems (`bm1383glv_register()`, `cxd56_i2cbus_initialize()`)
- `[cxd56_bm1422gmv_scu.c:board_bm1422gmv_initialize]` Initializes/registers kernel devices or filesystems (`bm1422gmv_register()`, `cxd56_i2cbus_initialize()`)

## Verification
- Run: `./tools/configure.sh sim:nsh && make`
