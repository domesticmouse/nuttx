# `samv71-xult/src` Component (`boards/arm/samv7/samv71-xult/src`)

## Overview
Board-level C implementation (`src`) for `samv71-xult` (`arm/samv7`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 24 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[atmxt-xpro.h:atmxt_config_s]` Type definition `atmxt_config_s`
- `[atmxt-xpro.h:HAVE_MAXTOUCH]` Hardware/board configuration macros (`HAVE_MAXTOUCH`, `HAVE_ILI9488_SMC`, `GPIO_ILI9488_RST`, `GPIO_ILI9488_BLOFF`, `GPIO_MXT_CHG`, `IRQ_MXT_CHG` (+7 more))
- `[samv71-xult.h:sam_sdram_config]` Public declaration `sam_sdram_config()`
- `[samv71-xult.h:sam_bringup]` Public declaration `sam_bringup()`
- `[samv71-xult.h:sam_spidev_initialize]` Public declaration `sam_spidev_initialize()`
- `[samv71-xult.h:sam_can_setup]` Public declaration `sam_can_setup()`
- `[samv71-xult.h:sam_usbinitialize]` Public declaration `sam_usbinitialize()`
- `[samv71-xult.h:sam_netinitialize]` Public declaration `sam_netinitialize()`
- `[samv71-xult.h:sam_emac0_setmac]` Public declaration `sam_emac0_setmac()`
- `[samv71-xult.h:sam_at24config]` Public declaration `sam_at24config()`
- `[samv71-xult.h:sam_tsc_setup]` Public declaration `sam_tsc_setup()`
- `[samv71-xult.h:sam_wm8904_initialize]` Public declaration `sam_wm8904_initialize()`
- `[samv71-xult.h:sam_audio_null_initialize]` Public declaration `sam_audio_null_initialize()`
- `[samv71-xult.h:sam_mrf24j40_initialize]` Public declaration `sam_mrf24j40_initialize()`
- `[samv71-xult.h:HAVE_HSMCI]` Hardware/board configuration macros (`HAVE_HSMCI`, `HAVE_AUTOMOUNTER`, `HAVE_USB`, `HAVE_USBDEV`, `HAVE_USBMONITOR`, `HAVE_NETWORK` (+60 more))
- `[sam_at24config.c:sam_at24config]` Public function `sam_at24config()`
- `[sam_atmxtconfig.c:g_atmxt_config]` Exported global symbol `g_atmxt_config`
- `[sam_audio_null.c:sam_audio_null_initialize]` Public function `sam_audio_null_initialize()`
- `[sam_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[sam_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[sam_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[sam_boardctl.c:board_ioctl]` Public function `board_ioctl()`
- `[sam_boardctl.c:board_uniqueid]` Public function `board_uniqueid()`
- `[sam_boot.c:sam_boardinitialize]` Public function `sam_boardinitialize()`
- *(+35 additional symbols across 24 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_AUDIO_NULL`, `CONFIG_AUDIO_WM8904`, `CONFIG_BOARDCTL` (+17 more)
- `[samv71-xult.h:#error]` Compile-time guard: `SAMV71 has only one MMC/SD slot (CONFIG_NSH_MMCSDSLOTNO)`
- `[sam_at24config.c:sam_at24config]` Validates preconditions and returns `-ENODEV` on failure
- `[sam_audio_null.c:DEBUGASSERT]` Requires `minor >= 0 && minor <= 25`
- `[sam_boardctl.c:board_ioctl]` Validates preconditions and returns `-EINVAL`, `-ENOTTY` on failure
- `[sam_boot.c:DEBUGASSERT]` Requires `frequency >= (BOARD_MAINOSC_FREQUENCY / 256)`
- `[sam_boot.c:DEBUGASSERT]` Requires `actual == frequency`
- `[sam_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL`, `-ENOSYS` on failure
- `[sam_composite.c:DEBUGASSERT]` Requires `g_mschandle == NULL`
- `[sam_composite.c:DEBUGASSERT]` Requires `g_mschandle != NULL`
- `[sam_ethernet.c:DEBUGASSERT]` Requires `intf`
- `[sam_ili9488.c:DEBUGASSERT]` Requires `nbytes <= 4`

## Side Effects
- `[sam_at24config.c:sam_at24config]` Initializes/registers kernel devices or filesystems (`at24c_initialize()`, `mtdconfig_register()`, `sam_i2cbus_initialize()`)
- `[sam_audio_null.c:sam_audio_null_initialize]` Initializes/registers kernel devices or filesystems (`audio_null_initialize()`, `audio_register()`, `pcm_decode_initialize()`)
- `[sam_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[sam_boot.c:sam_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `sam_spidev_initialize()`)
- `[sam_bringup.c:sam_bringup]` Initializes/registers kernel devices or filesystems (`board_oa_tc6_initialize()`, `dsxxxx_rtc_initialize()`, `fb_register()`, `i2c_register()`, `nx_mount()`)
- `[sam_buttons.c:board_button_initialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[sam_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[sam_buttons.c:board_button_initialize]` Modifies interrupt controller or critical-section state
- `[sam_composite.c:board_composite_initialize]` Initializes/registers kernel devices or filesystems (`composite_initialize()`)
- `[sam_ethernet.c:sam_netinitialize]` Configures or drives hardware GPIO pins
- `[sam_ethernet.c:sam_netinitialize]` Initializes/registers kernel devices or filesystems (`at24c_initialize()`, `sam_i2cbus_initialize()`)
- `[sam_ethernet.c:sam_netinitialize]` Modifies interrupt controller or critical-section state

## Verification
- Run: `./tools/configure.sh samv71-xult:nsh && make`
