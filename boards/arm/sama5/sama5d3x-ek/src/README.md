# `sama5d3x-ek/src` Component (`boards/arm/sama5/sama5d3x-ek/src`)

## Overview
Board-level C implementation (`src`) for `sama5d3x-ek` (`arm/sama5`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 23 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[sama5d3x-ek.h:sam_spidev_initialize]` Public declaration `sam_spidev_initialize()`
- `[sama5d3x-ek.h:sam_sdram_config]` Public declaration `sam_sdram_config()`
- `[sama5d3x-ek.h:sam_nand_automount]` Public declaration `sam_nand_automount()`
- `[sama5d3x-ek.h:sam_at25_automount]` Public declaration `sam_at25_automount()`
- `[sama5d3x-ek.h:sam_at24_automount]` Public declaration `sam_at24_automount()`
- `[sama5d3x-ek.h:sam_hsmci_initialize]` Public declaration `sam_hsmci_initialize()`
- `[sama5d3x-ek.h:sam_cardinserted]` Public declaration `sam_cardinserted()`
- `[sama5d3x-ek.h:sam_writeprotected]` Public declaration `sam_writeprotected()`
- `[sama5d3x-ek.h:sam_usbinitialize]` Public declaration `sam_usbinitialize()`
- `[sama5d3x-ek.h:sam_usbhost_initialize]` Public declaration `sam_usbhost_initialize()`
- `[sama5d3x-ek.h:sam_netinitialize]` Public declaration `sam_netinitialize()`
- `[sama5d3x-ek.h:sam_tsc_setup]` Public declaration `sam_tsc_setup()`
- `[sama5d3x-ek.h:sam_pwm_setup]` Public declaration `sam_pwm_setup()`
- `[sama5d3x-ek.h:sam_adc_setup]` Public declaration `sam_adc_setup()`
- `[sama5d3x-ek.h:sam_can_setup]` Public declaration `sam_can_setup()`
- `[sama5d3x-ek.h:sam_wm8904_initialize]` Public declaration `sam_wm8904_initialize()`
- `[sama5d3x-ek.h:HAVE_HSMCI]` Hardware/board configuration macros (`HAVE_HSMCI`, `HAVE_AT24`, `HAVE_AT25`, `HAVE_NAND`, `HAVE_USBHOST`, `HAVE_USBDEV` (+45 more))
- `[nor_main.c:void]` Public function `void()`
- `[nor_main.c:nor_main]` Public function `nor_main()`
- `[sam_adc.c:sam_adc_setup]` Public function `sam_adc_setup()`
- `[sam_at24.c:sam_at24_automount]` Public function `sam_at24_automount()`
- `[sam_at25.c:sam_at25_automount]` Public function `sam_at25_automount()`
- `[sam_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- *(+37 additional symbols across 23 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ADC`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_AUDIO_I2SCHAR`, `CONFIG_AUDIO_WM8904`, `CONFIG_CAN` (+21 more)
- `[sam_adc.c:sam_adc_setup]` Validates preconditions and returns `-ENODEV`, `-ENOSYS` on failure
- `[sam_at24.c:sam_at24_automount]` Validates preconditions and returns `-ENODEV` on failure
- `[sam_at25.c:sam_at25_automount]` Validates preconditions and returns `-ENODEV` on failure
- `[sam_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[sam_can.c:sam_can_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[sam_ethernet.c:DEBUGASSERT]` Requires `intf`
- `[sam_hsmci.c:sam_cardinserted_internal]` Validates preconditions and returns `-EINVAL`, `-ENODEV` on failure
- `[sam_i2schar.c:i2schar_devinit]` Validates preconditions and returns `-ENODEV` on failure
- `[sam_nandflash.c:board_nandflash_config]` Validates preconditions and returns `-ENODEV` on failure
- `[sam_pwm.c:sam_pwm_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[sam_sdram.c:#error]` Compile-time guard: `Unknown SDRAM type`

## Side Effects
- `[nor_main.c:void]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[sam_adc.c:sam_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`, `sam_adc_initialize()`)
- `[sam_at24.c:sam_at24_automount]` Initializes/registers kernel devices or filesystems (`at24c_initialize()`, `nx_mount()`, `nxffs_initialize()`, `sam_i2cbus_initialize()`)
- `[sam_at25.c:sam_at25_automount]` Initializes/registers kernel devices or filesystems (`at25_initialize()`, `nx_mount()`, `nxffs_initialize()`, `sam_spibus_initialize()`)
- `[sam_boot.c:sam_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `nx_mount()`, `sam_hsmci_initialize()`, `sam_spidev_initialize()`, `sam_usbhost_initialize()`)
- `[sam_buttons.c:board_button_initialize]` Modifies interrupt controller or critical-section state
- `[sam_can.c:sam_can_setup]` Initializes/registers kernel devices or filesystems (`can_register()`)
- `[sam_ethernet.c:sam_netinitialize]` Modifies interrupt controller or critical-section state
- `[sam_hsmci.c:sam_cardinserted_internal]` Initializes/registers kernel devices or filesystems (`sdio_initialize()`)
- `[sam_hsmci.c:sam_cardinserted_internal]` Modifies interrupt controller or critical-section state
- `[sam_i2schar.c:i2schar_devinit]` Initializes/registers kernel devices or filesystems (`i2schar_register()`, `sam_ssc_initialize()`)
- `[sam_nandflash.c:board_nandflash_config]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)

## Verification
- Run: `./tools/configure.sh sama5d3x-ek:nsh && make`
