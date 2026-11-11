# `jupiter-nano/src` Component (`boards/arm/sama5/jupiter-nano/src`)

## Overview
Board-level C implementation (`src`) for `jupiter-nano` (`arm/sama5`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 21 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[jupiter-nano.h:sam_bringup]` Public declaration `sam_bringup()`
- `[jupiter-nano.h:sam_sdmmc_initialize]` Public declaration `sam_sdmmc_initialize()`
- `[jupiter-nano.h:sam_cardinserted]` Public declaration `sam_cardinserted()`
- `[jupiter-nano.h:sam_writeprotected]` Public declaration `sam_writeprotected()`
- `[jupiter-nano.h:sam_usbinitialize]` Public declaration `sam_usbinitialize()`
- `[jupiter-nano.h:sam_usbhost_initialize]` Public declaration `sam_usbhost_initialize()`
- `[jupiter-nano.h:HAVE_SDMMC]` Hardware/board configuration macros (`HAVE_SDMMC`, `HAVE_AT25`, `HAVE_NAND`, `HAVE_USBHOST`, `HAVE_USBDEV`, `HAVE_USBMONITOR` (+22 more))
- `[etc_romfs.c:romfs_img]` Module symbol `romfs_img`
- `[sam_adc.c:sam_adc_setup]` Public function `sam_adc_setup()`
- `[sam_ajoystick.c:sam_ajoy_initialization]` Public function `sam_ajoy_initialization()`
- `[sam_at25.c:sam_at25_automount]` Public function `sam_at25_automount()`
- `[sam_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[sam_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[sam_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[sam_boot.c:sam_boardinitialize]` Public function `sam_boardinitialize()`
- `[sam_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[sam_bringup.c:sam_bringup]` Public function `sam_bringup()`
- `[sam_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[sam_buttons.c:board_buttons]` Public function `board_buttons()`
- `[sam_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[sam_can.c:sam_can_setup]` Public function `sam_can_setup()`
- `[sam_ethernet.c:sam_netinitialize]` Public function `sam_netinitialize()`
- `[sam_ethernet.c:arch_phy_irq]` Public function `arch_phy_irq()`
- `[sam_i2schar.c:i2schar_devinit]` Public function `i2schar_devinit()`
- *(+23 additional symbols across 21 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ADC`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_AUDIO_I2SCHAR`, `CONFIG_BOARDCTL_RESET`, `CONFIG_CAN` (+19 more)
- `[sam_adc.c:sam_adc_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[sam_ajoystick.c:DEBUGASSERT]` Requires `g_ajoyhandler`
- `[sam_ajoystick.c:#error]` Compile-time guard: `CONFIG_ADC is required for the Itead joystick`
- `[sam_ajoystick.c:#error]` Compile-time guard: `CONFIG_SAMA5_ADC_CHAN0 and 1 are required for Itead joystick`
- `[sam_at25.c:sam_at25_automount]` Validates preconditions and returns `-ENODEV` on failure
- `[sam_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[sam_can.c:sam_can_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[sam_ethernet.c:DEBUGASSERT]` Requires `intf`
- `[sam_i2schar.c:i2schar_devinit]` Validates preconditions and returns `-ENODEV` on failure
- `[sam_nandflash.c:board_nandflash_config]` Validates preconditions and returns `-ENODEV` on failure
- `[sam_pwm.c:sam_pwm_setup]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[sam_adc.c:sam_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`, `sam_adc_initialize()`)
- `[sam_ajoystick.c:sam_ajoy_initialization]` Initializes/registers kernel devices or filesystems (`ajoy_register()`)
- `[sam_ajoystick.c:sam_ajoy_initialization]` Modifies interrupt controller or critical-section state
- `[sam_at25.c:sam_at25_automount]` Initializes/registers kernel devices or filesystems (`at25_initialize()`, `nx_mount()`, `nxffs_initialize()`, `sam_spibus_initialize()`)
- `[sam_boot.c:sam_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[sam_bringup.c:sam_bringup]` Initializes/registers kernel devices or filesystems (`cdcecm_initialize()`, `i2c_register()`, `nsh_sdmmc_initialize()`, `nx_mount()`, `romdisk_register()`)
- `[sam_buttons.c:board_button_initialize]` Modifies interrupt controller or critical-section state
- `[sam_can.c:sam_can_setup]` Initializes/registers kernel devices or filesystems (`can_register()`)
- `[sam_ethernet.c:sam_netinitialize]` Modifies interrupt controller or critical-section state
- `[sam_i2schar.c:i2schar_devinit]` Initializes/registers kernel devices or filesystems (`i2schar_register()`, `sam_ssc_initialize()`)
- `[sam_nandflash.c:board_nandflash_config]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[sam_nandflash.c:board_nandflash_config]` Initializes/registers kernel devices or filesystems (`nx_mount()`, `nxffs_initialize()`, `sam_nand_initialize()`)

## Verification
- Run: `./tools/configure.sh jupiter-nano:nsh && make`
