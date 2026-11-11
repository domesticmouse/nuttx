# `olimex-lpc-h3131/src` Component (`boards/arm/lpc31xx/olimex-lpc-h3131/src`)

## Overview
Board-level C implementation (`src`) for `olimex-lpc-h3131` (`arm/lpc31xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[lpc_h3131.h:lpc31_meminitialize]` Public declaration `lpc31_meminitialize()`
- `[lpc_h3131.h:lpc31_spidev_initialize]` Public declaration `lpc31_spidev_initialize()`
- `[lpc_h3131.h:lpc31_usbdev_initialize]` Public declaration `lpc31_usbdev_initialize()`
- `[lpc_h3131.h:lpc31_usbhost_bootinitialize]` Public declaration `lpc31_usbhost_bootinitialize()`
- `[lpc_h3131.h:lpc31_usbhost_initialize]` Public declaration `lpc31_usbhost_initialize()`
- `[lpc_h3131.h:HAVE_MMCSD]` Hardware/board configuration macros (`HAVE_MMCSD`, `HAVE_USBHOST`, `HAVE_USBMONITOR`, `CONFIG_NSH_MMCSDMINOR`, `GPIO_LED1`, `GPIO_LED2` (+3 more))
- `[lpc31_boot.c:lpc31_boardinitialize]` Public function `lpc31_boardinitialize()`
- `[lpc31_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[lpc31_clkinit.c:g_boardclks]` Exported global symbol `g_boardclks`
- `[lpc31_leds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[lpc31_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[lpc31_leds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[lpc31_leds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[lpc31_leds.c:board_userled]` Public function `board_userled()`
- `[lpc31_leds.c:board_userled_all]` Public function `board_userled_all()`
- `[lpc31_mem.c:lpc31_meminitialize]` Public function `lpc31_meminitialize()`
- `[lpc31_mmcsd.c:lpc31_mmcsd_initialize]` Public function `lpc31_mmcsd_initialize()`
- `[lpc31_spi.c:lpc31_spidev_initialize]` Public function `lpc31_spidev_initialize()`
- `[lpc31_spi.c:lpc31_spiselect]` Public function `lpc31_spiselect()`
- `[lpc31_spi.c:lpc31_spistatus]` Public function `lpc31_spistatus()`
- `[lpc31_usbhost.c:lpc31_usbhost_bootinitialize]` Public function `lpc31_usbhost_bootinitialize()`
- `[lpc31_usbhost.c:lpc31_usbhost_initialize]` Public function `lpc31_usbhost_initialize()`
- `[lpc31_usbhost.c:lpc31_usbhost_vbusdrive]` Public function `lpc31_usbhost_vbusdrive()`
- `[lpc31_usbhost.c:lpc31_setup_overcurrent]` Public function `lpc31_setup_overcurrent()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_LEDS`, `CONFIG_LPC31_EXTDRAM`, `CONFIG_LPC31_MCI`, `CONFIG_LPC31_SPI`, `CONFIG_LPC31_USBOTG`, `CONFIG_USBHOST`
- `[lpc31_boot.c:#error]` Compile-time guard: `Only one MMC/SD slot`
- `[lpc31_mmcsd.c:lpc31_mmcsd_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[lpc31_usbhost.c:lpc31_usbhost_bootinitialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[lpc_h3131.h:lpc31_meminitialize]` Initializes/registers kernel devices or filesystems (`lpc31_mmcsd_initialize()`)
- `[lpc31_boot.c:lpc31_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `lpc31_mmcsd_initialize()`, `lpc31_spidev_initialize()`, `lpc31_usbdev_initialize()`, `lpc31_usbhost_initialize()`)
- `[lpc31_mem.c:lpc31_meminitialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[lpc31_mmcsd.c:lpc31_mmcsd_initialize]` Initializes/registers kernel devices or filesystems (`sdio_initialize()`)
- `[lpc31_usbhost.c:lpc31_usbhost_bootinitialize]` Initializes/registers kernel devices or filesystems (`lpc31_ehci_initialize()`, `usbhost_cdcacm_initialize()`, `usbhost_hub_initialize()`, `usbhost_msc_initialize()`)
- `[lpc31_usbhost.c:lpc31_usbhost_bootinitialize]` Modifies interrupt controller or critical-section state

## Verification
- Run: `./tools/configure.sh olimex-lpc-h3131:nsh && make`
