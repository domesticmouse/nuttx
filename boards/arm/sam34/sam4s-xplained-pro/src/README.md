# `sam4s-xplained-pro/src` Component (`boards/arm/sam34/sam4s-xplained-pro/src`)

## Overview
Board-level C implementation (`src`) for `sam4s-xplained-pro` (`arm/sam34`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 10 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[sam4s-xplained-pro.h:sam_nand_automount]` Public declaration `sam_nand_automount()`
- `[sam4s-xplained-pro.h:sam_hsmci_initialize]` Public declaration `sam_hsmci_initialize()`
- `[sam4s-xplained-pro.h:sam_sdinitialize]` Public declaration `sam_sdinitialize()`
- `[sam4s-xplained-pro.h:sam_cardinserted]` Public declaration `sam_cardinserted()`
- `[sam4s-xplained-pro.h:sam_writeprotected]` Public declaration `sam_writeprotected()`
- `[sam4s-xplained-pro.h:sam_watchdog_initialize]` Public declaration `sam_watchdog_initialize()`
- `[sam4s-xplained-pro.h:HAVE_HSMCI]` Hardware/board configuration macros (`HAVE_HSMCI`, `HAVE_PROC`, `HAVE_USBDEV`, `HAVE_NAND`, `HAVE_MMCSD_SPI`, `CONFIG_NSH_MMCSDMINOR` (+12 more))
- `[sam_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[sam_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[sam_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[sam_boot.c:sam_boardinitialize]` Public function `sam_boardinitialize()`
- `[sam_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[sam_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[sam_buttons.c:board_buttons]` Public function `board_buttons()`
- `[sam_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[sam_hsmci.c:sam_hsmci_initialize]` Public function `sam_hsmci_initialize()`
- `[sam_hsmci.c:sam_cardinserted]` Public function `sam_cardinserted()`
- `[sam_hsmci.c:sam_writeprotected]` Public function `sam_writeprotected()`
- `[sam_nandflash.c:board_nandflash_config]` Public function `board_nandflash_config()`
- `[sam_nandflash.c:sam_nand_automount]` Public function `sam_nand_automount()`
- `[sam_spi.c:sam_spidev_initialize]` Public function `sam_spidev_initialize()`
- `[sam_spi.c:sam_spi0select]` Public function `sam_spi0select()`
- `[sam_spi.c:sam_spi0status]` Public function `sam_spi0status()`
- *(+6 additional symbols across 10 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_MMCSD_SPI`, `CONFIG_MTD_NAND`, `CONFIG_SAM34_EXTNAND`, `CONFIG_SAM34_HSMCI` (+2 more)
- `[sam_boot.c:DEBUGASSERT]` Requires `check >= 0`
- `[sam_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[sam_hsmci.c:sam_hsmci_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[sam_nandflash.c:board_nandflash_config]` Validates preconditions and returns `-ENODEV` on failure
- `[sam_spi.c:sam_spidev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[sam_wdt.c:DEBUGASSERT]` Requires `taskid > 0`
- `[sam_wdt.c:#error]` Compile-time guard: `WDT_THREAD_INTERVAL must be greater than or equal to WDT_MINTIME`

## Side Effects
- `[sam_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[sam_boot.c:sam_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `cdcacm_initialize()`, `nx_mount()`, `sam_hsmci_initialize()`, `sam_led_initialize()`)
- `[sam_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[sam_buttons.c:board_button_initialize]` Modifies interrupt controller or critical-section state
- `[sam_hsmci.c:sam_hsmci_initialize]` Configures or drives hardware GPIO pins
- `[sam_hsmci.c:sam_hsmci_initialize]` Initializes/registers kernel devices or filesystems (`sdio_initialize()`)
- `[sam_hsmci.c:sam_hsmci_initialize]` Modifies interrupt controller or critical-section state
- `[sam_nandflash.c:board_nandflash_config]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[sam_nandflash.c:board_nandflash_config]` Configures or drives hardware GPIO pins
- `[sam_nandflash.c:board_nandflash_config]` Initializes/registers kernel devices or filesystems (`nx_mount()`, `nxffs_initialize()`, `sam_nand_initialize()`)
- `[sam_spi.c:sam_spidev_initialize]` Configures or drives hardware GPIO pins
- `[sam_spi.c:sam_spidev_initialize]` Initializes/registers kernel devices or filesystems (`sam_spibus_initialize()`)

## Verification
- Run: `./tools/configure.sh sam4s-xplained-pro:nsh && make`
