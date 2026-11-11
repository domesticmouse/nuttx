# `same70-xplained/src` Component (`boards/arm/samv7/same70-xplained/src`)

## Overview
Board-level C implementation (`src`) for `same70-xplained` (`arm/samv7`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 18 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[same70-xplained.h:sam_sdram_config]` Public declaration `sam_sdram_config()`
- `[same70-xplained.h:sam_bringup]` Public declaration `sam_bringup()`
- `[same70-xplained.h:sam_afec_setup]` Public declaration `sam_afec_setup()`
- `[same70-xplained.h:sam_pwm_setup]` Public declaration `sam_pwm_setup()`
- `[same70-xplained.h:sam_dacdev_initialize]` Public declaration `sam_dacdev_initialize()`
- `[same70-xplained.h:sam_spidev_initialize]` Public declaration `sam_spidev_initialize()`
- `[same70-xplained.h:sam_usbinitialize]` Public declaration `sam_usbinitialize()`
- `[same70-xplained.h:sam_can_setup]` Public declaration `sam_can_setup()`
- `[same70-xplained.h:sam_netinitialize]` Public declaration `sam_netinitialize()`
- `[same70-xplained.h:sam_emac0_setmac]` Public declaration `sam_emac0_setmac()`
- `[same70-xplained.h:sam_at24config]` Public declaration `sam_at24config()`
- `[same70-xplained.h:sam_mrf24j40_initialize]` Public declaration `sam_mrf24j40_initialize()`
- `[same70-xplained.h:sam_xbee_initialize]` Public declaration `sam_xbee_initialize()`
- `[same70-xplained.h:HAVE_HSMCI]` Hardware/board configuration macros (`HAVE_HSMCI`, `HAVE_AUTOMOUNTER`, `HAVE_USB`, `HAVE_USBDEV`, `HAVE_USBMONITOR`, `HAVE_NETWORK` (+31 more))
- `[sam_afec.c:sam_afec_setup]` Public function `sam_afec_setup()`
- `[sam_at24config.c:sam_at24config]` Public function `sam_at24config()`
- `[sam_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[sam_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[sam_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[sam_boardctl.c:board_ioctl]` Public function `board_ioctl()`
- `[sam_boardctl.c:board_uniqueid]` Public function `board_uniqueid()`
- `[sam_boot.c:sam_boardinitialize]` Public function `sam_boardinitialize()`
- `[sam_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[sam_bringup.c:sam_bringup]` Public function `sam_bringup()`
- *(+23 additional symbols across 18 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_BOARDCTL`, `CONFIG_IEEE802154_MRF24J40`, `CONFIG_IEEE802154_XBEE` (+13 more)
- `[same70-xplained.h:#error]` Compile-time guard: `SAME70 has only one MMC/SD slot (CONFIG_NSH_MMCSDSLOTNO)`
- `[sam_afec.c:sam_afec_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[sam_at24config.c:sam_at24config]` Validates preconditions and returns `-ENODEV` on failure
- `[sam_boardctl.c:board_ioctl]` Validates preconditions and returns `-EINVAL`, `-ENOTTY` on failure
- `[sam_boot.c:DEBUGASSERT]` Requires `frequency >= (BOARD_MAINOSC_FREQUENCY / 256)`
- `[sam_boot.c:DEBUGASSERT]` Requires `actual == frequency`
- `[sam_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[sam_dac.c:sam_dacdev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[sam_ethernet.c:DEBUGASSERT]` Requires `intf`
- `[sam_mcan.c:sam_can_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[sam_mrf24j40.c:DEBUGASSERT]` Requires `priv != NULL`

## Side Effects
- `[sam_afec.c:sam_afec_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`, `sam_afec_initialize()`)
- `[sam_at24config.c:sam_at24config]` Initializes/registers kernel devices or filesystems (`at24c_initialize()`, `mtdconfig_register()`, `sam_i2cbus_initialize()`)
- `[sam_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[sam_boot.c:sam_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `sam_spidev_initialize()`)
- `[sam_bringup.c:sam_bringup]` Initializes/registers kernel devices or filesystems (`i2c_register()`, `nx_mount()`, `romdisk_register()`, `sam_automount_initialize()`, `sam_dacdev_initialize()`)
- `[sam_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[sam_buttons.c:board_button_initialize]` Modifies interrupt controller or critical-section state
- `[sam_dac.c:sam_dacdev_initialize]` Initializes/registers kernel devices or filesystems (`dac_register()`, `sam_dac_initialize()`)
- `[sam_ethernet.c:sam_netinitialize]` Configures or drives hardware GPIO pins
- `[sam_ethernet.c:sam_netinitialize]` Initializes/registers kernel devices or filesystems (`at24c_initialize()`, `sam_i2cbus_initialize()`)
- `[sam_ethernet.c:sam_netinitialize]` Modifies interrupt controller or critical-section state
- `[sam_mcan.c:sam_can_setup]` Initializes/registers kernel devices or filesystems (`can_register()`, `sam_mcan_initialize()`)

## Verification
- Run: `./tools/configure.sh same70-xplained:nsh && make`
