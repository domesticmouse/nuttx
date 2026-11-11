# `giant-board/src` Component (`boards/arm/sama5/giant-board/src`)

## Overview
Board-level C implementation (`src`) for `giant-board` (`arm/sama5`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 15 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[giant-board.h:sam_bringup]` Public declaration `sam_bringup()`
- `[giant-board.h:sam_sdmmc_initialize]` Public declaration `sam_sdmmc_initialize()`
- `[giant-board.h:sam_cardinserted]` Public declaration `sam_cardinserted()`
- `[giant-board.h:sam_writeprotected]` Public declaration `sam_writeprotected()`
- `[giant-board.h:sam_usbinitialize]` Public declaration `sam_usbinitialize()`
- `[giant-board.h:sam_usbhost_initialize]` Public declaration `sam_usbhost_initialize()`
- `[giant-board.h:HAVE_SDMMC]` Hardware/board configuration macros (`HAVE_SDMMC`, `HAVE_USBHOST`, `HAVE_USBDEV`, `HAVE_USBMONITOR`, `HAVE_NETWORK`, `CONFIG_NSH_MMCSDMINOR` (+49 more))
- `[sam_adc.c:sam_adc_setup]` Public function `sam_adc_setup()`
- `[sam_ajoystick.c:sam_ajoy_initialization]` Public function `sam_ajoy_initialization()`
- `[sam_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[sam_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[sam_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[sam_boot.c:sam_boardinitialize]` Public function `sam_boardinitialize()`
- `[sam_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[sam_bringup.c:sam_bringup]` Public function `sam_bringup()`
- `[sam_i2schar.c:i2schar_devinit]` Public function `i2schar_devinit()`
- `[sam_pwm.c:sam_pwm_setup]` Public function `sam_pwm_setup()`
- `[sam_reset.c:board_reset]` Public function `board_reset()`
- `[sam_sdmmc.c:sam_cardinserted_internal]` Public function `sam_cardinserted_internal()`
- `[sam_sdmmc.c:sam_sdmmc_initialize]` Public function `sam_sdmmc_initialize()`
- `[sam_sdmmc.c:sam_cardinserted]` Public function `sam_cardinserted()`
- `[sam_sdmmc.c:sam_writeprotected]` Public function `sam_writeprotected()`
- `[sam_sdram.c:sam_sdram_config]` Public function `sam_sdram_config()`
- `[sam_spi.c:sam_spidev_initialize]` Public function `sam_spidev_initialize()`
- *(+13 additional symbols across 15 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ADC`, `CONFIG_ARCH_LEDS`, `CONFIG_AUDIO_I2SCHAR`, `CONFIG_BOARDCTL_RESET`, `CONFIG_INPUT_AJOYSTICK`, `CONFIG_PWM` (+12 more)
- `[sam_adc.c:sam_adc_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[sam_ajoystick.c:DEBUGASSERT]` Requires `g_ajoyhandler`
- `[sam_ajoystick.c:#error]` Compile-time guard: `CONFIG_ADC is required for the Itead joystick`
- `[sam_ajoystick.c:#error]` Compile-time guard: `CONFIG_SAMA5_ADC_CHAN0 and 1 are required for Itead joystick`
- `[sam_i2schar.c:i2schar_devinit]` Validates preconditions and returns `-ENODEV` on failure
- `[sam_pwm.c:sam_pwm_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[sam_sdmmc.c:sam_cardinserted_internal]` Validates preconditions and returns `-EINVAL`, `-ENODEV` on failure
- `[sam_sdram.c:#error]` Compile-time guard: `Unknown SDRAM type`
- `[sam_usb.c:sam_usbinitialize]` Validates preconditions and returns `-ENODEV` on failure
- `[sam_usbmsc.c:#error]` Compile-time guard: `AT25 Serial FLASH not supported`
- `[sam_usbmsc.c:#error]` Compile-time guard: `AT25 FTL support required (CONFIG_SAMA5D3XPLAINED_AT25_FTL)`

## Side Effects
- `[sam_adc.c:sam_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`, `sam_adc_initialize()`)
- `[sam_ajoystick.c:sam_ajoy_initialization]` Initializes/registers kernel devices or filesystems (`ajoy_register()`)
- `[sam_ajoystick.c:sam_ajoy_initialization]` Modifies interrupt controller or critical-section state
- `[sam_boot.c:sam_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[sam_bringup.c:sam_bringup]` Initializes/registers kernel devices or filesystems (`cdcecm_initialize()`, `i2c_register()`, `nsh_sdmmc_initialize()`, `nx_mount()`, `romdisk_register()`)
- `[sam_i2schar.c:i2schar_devinit]` Initializes/registers kernel devices or filesystems (`i2schar_register()`, `sam_ssc_initialize()`)
- `[sam_pwm.c:sam_pwm_setup]` Initializes/registers kernel devices or filesystems (`pwm_register()`)
- `[sam_sdmmc.c:sam_cardinserted_internal]` Initializes/registers kernel devices or filesystems (`sam_sdmmc_sdio_initialize()`)
- `[sam_sdmmc.c:sam_cardinserted_internal]` Modifies interrupt controller or critical-section state
- `[sam_sdram.c:sam_sdram_config]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[sam_usb.c:sam_usbinitialize]` Initializes/registers kernel devices or filesystems (`sam_ehci_initialize()`, `sam_ohci_initialize()`, `usbhost_cdcacm_initialize()`, `usbhost_hub_initialize()`, `usbhost_msc_initialize()`)
- `[sam_usb.c:sam_usbinitialize]` Modifies interrupt controller or critical-section state

## Verification
- Run: `./tools/configure.sh giant-board:nsh && make`
