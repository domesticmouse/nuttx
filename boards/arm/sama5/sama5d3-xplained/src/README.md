# `sama5d3-xplained/src` Component (`boards/arm/sama5/sama5d3-xplained/src`)

## Overview
Board-level C implementation (`src`) for `sama5d3-xplained` (`arm/sama5`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 20 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[sama5d3-xplained.h:sam_spidev_initialize]` Public declaration `sam_spidev_initialize()`
- `[sama5d3-xplained.h:sam_sdram_config]` Public declaration `sam_sdram_config()`
- `[sama5d3-xplained.h:sam_nand_automount]` Public declaration `sam_nand_automount()`
- `[sama5d3-xplained.h:sam_at25_automount]` Public declaration `sam_at25_automount()`
- `[sama5d3-xplained.h:sam_hsmci_initialize]` Public declaration `sam_hsmci_initialize()`
- `[sama5d3-xplained.h:sam_cardinserted]` Public declaration `sam_cardinserted()`
- `[sama5d3-xplained.h:sam_writeprotected]` Public declaration `sam_writeprotected()`
- `[sama5d3-xplained.h:sam_usbinitialize]` Public declaration `sam_usbinitialize()`
- `[sama5d3-xplained.h:sam_usbhost_initialize]` Public declaration `sam_usbhost_initialize()`
- `[sama5d3-xplained.h:sam_pwm_setup]` Public declaration `sam_pwm_setup()`
- `[sama5d3-xplained.h:sam_adc_setup]` Public declaration `sam_adc_setup()`
- `[sama5d3-xplained.h:sam_can_setup]` Public declaration `sam_can_setup()`
- `[sama5d3-xplained.h:sam_netinitialize]` Public declaration `sam_netinitialize()`
- `[sama5d3-xplained.h:sam_bringup]` Public declaration `sam_bringup()`
- `[sama5d3-xplained.h:HAVE_HSMCI]` Hardware/board configuration macros (`HAVE_HSMCI`, `HAVE_AT25`, `HAVE_NAND`, `HAVE_USBHOST`, `HAVE_USBDEV`, `HAVE_USBMONITOR` (+67 more))
- `[sam_adc.c:sam_adc_setup]` Public function `sam_adc_setup()`
- `[sam_ajoystick.c:sam_ajoy_initialization]` Public function `sam_ajoy_initialization()`
- `[sam_at25.c:sam_at25_automount]` Public function `sam_at25_automount()`
- `[sam_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[sam_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[sam_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[sam_boot.c:sam_boardinitialize]` Public function `sam_boardinitialize()`
- `[sam_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- *(+31 additional symbols across 20 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ADC`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_AUDIO_I2SCHAR`, `CONFIG_BOARDCTL_RESET`, `CONFIG_CAN` (+16 more)
- `[sam_adc.c:sam_adc_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[sam_ajoystick.c:DEBUGASSERT]` Requires `g_ajoyhandler`
- `[sam_ajoystick.c:#error]` Compile-time guard: `CONFIG_ADC is required for the Itead joystick`
- `[sam_ajoystick.c:#error]` Compile-time guard: `CONFIG_SAMA5_ADC_CHAN0 and 1 are required for Itead joystick`
- `[sam_at25.c:sam_at25_automount]` Validates preconditions and returns `-ENODEV` on failure
- `[sam_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[sam_can.c:sam_can_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[sam_ethernet.c:DEBUGASSERT]` Requires `intf`
- `[sam_hsmci.c:sam_cardinserted_internal]` Validates preconditions and returns `-EINVAL`, `-ENODEV` on failure
- `[sam_i2schar.c:i2schar_devinit]` Validates preconditions and returns `-ENODEV` on failure
- `[sam_nandflash.c:board_nandflash_config]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[sam_adc.c:sam_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`, `sam_adc_initialize()`)
- `[sam_ajoystick.c:sam_ajoy_initialization]` Initializes/registers kernel devices or filesystems (`ajoy_register()`)
- `[sam_ajoystick.c:sam_ajoy_initialization]` Modifies interrupt controller or critical-section state
- `[sam_at25.c:sam_at25_automount]` Initializes/registers kernel devices or filesystems (`at25_initialize()`, `nx_mount()`, `nxffs_initialize()`, `sam_spibus_initialize()`)
- `[sam_boot.c:sam_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `sam_spidev_initialize()`)
- `[sam_bringup.c:sam_bringup]` Initializes/registers kernel devices or filesystems (`cdcecm_initialize()`, `i2c_register()`, `nx_mount()`, `romdisk_register()`, `sam_audio_null_initialize()`)
- `[sam_buttons.c:board_button_initialize]` Modifies interrupt controller or critical-section state
- `[sam_can.c:sam_can_setup]` Initializes/registers kernel devices or filesystems (`can_register()`)
- `[sam_ethernet.c:sam_netinitialize]` Modifies interrupt controller or critical-section state
- `[sam_hsmci.c:sam_cardinserted_internal]` Initializes/registers kernel devices or filesystems (`sdio_initialize()`)
- `[sam_hsmci.c:sam_cardinserted_internal]` Modifies interrupt controller or critical-section state
- `[sam_i2schar.c:i2schar_devinit]` Initializes/registers kernel devices or filesystems (`i2schar_register()`, `sam_ssc_initialize()`)

## Verification
- Run: `./tools/configure.sh sama5d3-xplained:nsh && make`
