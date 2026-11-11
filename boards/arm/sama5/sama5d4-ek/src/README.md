# `sama5d4-ek/src` Component (`boards/arm/sama5/sama5d4-ek/src`)

## Overview
Board-level C implementation (`src`) for `sama5d4-ek` (`arm/sama5`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 24 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[sama5d4-ek.h:sam_spidev_initialize]` Public declaration `sam_spidev_initialize()`
- `[sama5d4-ek.h:sam_sdram_config]` Public declaration `sam_sdram_config()`
- `[sama5d4-ek.h:sam_bringup]` Public declaration `sam_bringup()`
- `[sama5d4-ek.h:sam_nand_automount]` Public declaration `sam_nand_automount()`
- `[sama5d4-ek.h:sam_at25_automount]` Public declaration `sam_at25_automount()`
- `[sama5d4-ek.h:sam_hsmci_initialize]` Public declaration `sam_hsmci_initialize()`
- `[sama5d4-ek.h:sam_cardinserted]` Public declaration `sam_cardinserted()`
- `[sama5d4-ek.h:sam_automount_initialize]` Public declaration `sam_automount_initialize()`
- `[sama5d4-ek.h:sam_automount_event]` Public declaration `sam_automount_event()`
- `[sama5d4-ek.h:sam_writeprotected]` Public declaration `sam_writeprotected()`
- `[sama5d4-ek.h:sam_usbinitialize]` Public declaration `sam_usbinitialize()`
- `[sama5d4-ek.h:sam_usbhost_initialize]` Public declaration `sam_usbhost_initialize()`
- `[sama5d4-ek.h:sam_tsc_setup]` Public declaration `sam_tsc_setup()`
- `[sama5d4-ek.h:sam_pwm_setup]` Public declaration `sam_pwm_setup()`
- `[sama5d4-ek.h:sam_adc_setup]` Public declaration `sam_adc_setup()`
- `[sama5d4-ek.h:sam_netinitialize]` Public declaration `sam_netinitialize()`
- `[sama5d4-ek.h:sam_wm8904_initialize]` Public declaration `sam_wm8904_initialize()`
- `[sama5d4-ek.h:sam_audio_null_initialize]` Public declaration `sam_audio_null_initialize()`
- `[sama5d4-ek.h:sam_pmic_initialize]` Public declaration `sam_pmic_initialize()`
- `[sama5d4-ek.h:HAVE_HSMCI]` Hardware/board configuration macros (`HAVE_HSMCI`, `HAVE_AT25`, `HAVE_NAND`, `HAVE_AUTOMOUNTER`, `HAVE_USBHOST`, `HAVE_USBDEV` (+67 more))
- `[at25_main.c:at25_main]` Public function `at25_main()`
- `[dram_main.c:void]` Public function `void()`
- `[dram_main.c:dram_main]` Public function `dram_main()`
- `[etc_romfs.c:romfs_img]` Module symbol `romfs_img`
- *(+41 additional symbols across 24 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ADC`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_AUDIO_NULL`, `CONFIG_AUDIO_WM8904`, `CONFIG_ETC_ROMFS` (+18 more)
- `[at25_main.c:#error]` Compile-time guard: `The AT25 Serial FLASH is not available`
- `[at25_main.c:#error]` Compile-time guard: `CONFIG_SAMA5D4EK_AT25_BLOCKMOUNT must be selected`
- `[sam_adc.c:sam_adc_setup]` Validates preconditions and returns `-ENODEV`, `-ENOSYS` on failure
- `[sam_at25.c:sam_at25_automount]` Validates preconditions and returns `-ENODEV` on failure
- `[sam_audio_null.c:DEBUGASSERT]` Requires `minor >= 0 && minor <= 25`
- `[sam_automount.c:DEBUGASSERT]` Requires `config && config->state`
- `[sam_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[sam_ethernet.c:DEBUGASSERT]` Requires `intf`
- `[sam_hsmci.c:sam_cardinserted_internal]` Validates preconditions and returns `-EINVAL`, `-ENODEV` on failure
- `[sam_maxtouch.c:DEBUGASSERT]` Requires `minor == 0`
- `[sam_nandflash.c:board_nandflash_config]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[dram_main.c:void]` Initializes/registers kernel devices or filesystems (`sam_pmic_initialize()`)
- `[sam_adc.c:sam_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`, `sam_adc_initialize()`)
- `[sam_at25.c:sam_at25_automount]` Initializes/registers kernel devices or filesystems (`at25_initialize()`, `nx_mount()`, `nxffs_initialize()`, `sam_spibus_initialize()`)
- `[sam_audio_null.c:sam_audio_null_initialize]` Initializes/registers kernel devices or filesystems (`audio_null_initialize()`, `audio_register()`, `pcm_decode_initialize()`)
- `[sam_automount.c:sam_automount_initialize]` Initializes/registers kernel devices or filesystems (`automount_initialize()`)
- `[sam_automount.c:sam_automount_initialize]` Modifies interrupt controller or critical-section state
- `[sam_boot.c:sam_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `sam_spidev_initialize()`)
- `[sam_bringup.c:sam_bringup]` Initializes/registers kernel devices or filesystems (`i2c_register()`, `nx_mount()`, `romdisk_register()`, `sam_audio_null_initialize()`, `sam_automount_initialize()`)
- `[sam_buttons.c:board_button_initialize]` Modifies interrupt controller or critical-section state
- `[sam_ethernet.c:sam_netinitialize]` Modifies interrupt controller or critical-section state
- `[sam_hsmci.c:sam_cardinserted_internal]` Initializes/registers kernel devices or filesystems (`sdio_initialize()`)
- `[sam_hsmci.c:sam_cardinserted_internal]` Modifies interrupt controller or critical-section state

## Verification
- Run: `./tools/configure.sh sama5d4-ek:nsh && make`
