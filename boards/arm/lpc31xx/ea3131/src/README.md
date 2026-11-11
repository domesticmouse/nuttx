# `ea3131/src` Component (`boards/arm/lpc31xx/ea3131/src`)

## Overview
Board-level C implementation (`src`) for `ea3131` (`arm/lpc31xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 9 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[ea3131.h:lpc31_meminitialize]` Public declaration `lpc31_meminitialize()`
- `[ea3131.h:lpc31_spidev_initialize]` Public declaration `lpc31_spidev_initialize()`
- `[ea3131.h:lpc31_usbdev_initialize]` Public declaration `lpc31_usbdev_initialize()`
- `[ea3131.h:lpc31_usbhost_bootinitialize]` Public declaration `lpc31_usbhost_bootinitialize()`
- `[ea3131.h:lpc31_usbhost_initialize]` Public declaration `lpc31_usbhost_initialize()`
- `[ea3131.h:lpc31_pginitialize]` Public declaration `lpc31_pginitialize()`
- `[ea3131.h:SPINOR_CS]` Hardware/board configuration macros (`SPINOR_CS`)
- `[lpc31_boot.c:lpc31_boardinitialize]` Public function `lpc31_boardinitialize()`
- `[lpc31_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[lpc31_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[lpc31_buttons.c:board_buttons]` Public function `board_buttons()`
- `[lpc31_clkinit.c:g_boardclks]` Exported global symbol `g_boardclks`
- `[lpc31_fillpage.c:up_fillpage]` Public function `up_fillpage()`
- `[lpc31_fillpage.c:lpc31_pginitialize]` Public function `lpc31_pginitialize()`
- `[lpc31_leds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[lpc31_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[lpc31_leds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[lpc31_mem.c:lpc31_meminitialize]` Public function `lpc31_meminitialize()`
- `[lpc31_spi.c:lpc31_spidev_initialize]` Public function `lpc31_spidev_initialize()`
- `[lpc31_spi.c:lpc31_spiselect]` Public function `lpc31_spiselect()`
- `[lpc31_spi.c:lpc31_spistatus]` Public function `lpc31_spistatus()`
- `[lpc31_usbhost.c:lpc31_usbhost_bootinitialize]` Public function `lpc31_usbhost_bootinitialize()`
- `[lpc31_usbhost.c:lpc31_usbhost_initialize]` Public function `lpc31_usbhost_initialize()`
- `[lpc31_usbhost.c:lpc31_usbhost_vbusdrive]` Public function `lpc31_usbhost_vbusdrive()`
- *(+1 additional symbols across 9 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_LEGACY_PAGING`, `CONFIG_LPC31_EXTDRAM`, `CONFIG_LPC31_SPI`, `CONFIG_LPC31_USBOTG` (+1 more)
- `[lpc31_boot.c:#error]` Compile-time guard: `Only one MMC/SD slot`
- `[lpc31_boot.c:#error]` Compile-time guard: `Unrecognized LPC31XX board`
- `[lpc31_fillpage.c:DEBUGASSERT]` Requires `sdio != NULL`
- `[lpc31_fillpage.c:DEBUGASSERT]` Requires `ret == OK`
- `[lpc31_fillpage.c:#error]` Compile-time guard: `Only one SD slot`
- `[lpc31_fillpage.c:#error]` Compile-time guard: `Unrecognized LPC31XX board`
- `[lpc31_usbhost.c:lpc31_usbhost_bootinitialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[lpc31_boot.c:lpc31_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `lpc31_spidev_initialize()`, `lpc31_usbdev_initialize()`, `sdio_initialize()`)
- `[lpc31_fillpage.c:up_fillpage]` Initializes/registers kernel devices or filesystems (`at45db_initialize()`, `lpc31_spibus_initialize()`, `m25p_initialize()`, `nx_mount()`, `sdio_initialize()`)
- `[lpc31_mem.c:lpc31_meminitialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[lpc31_usbhost.c:lpc31_usbhost_bootinitialize]` Initializes/registers kernel devices or filesystems (`lpc31_ehci_initialize()`, `usbhost_cdcacm_initialize()`, `usbhost_hub_initialize()`, `usbhost_msc_initialize()`)
- `[lpc31_usbhost.c:lpc31_usbhost_bootinitialize]` Modifies interrupt controller or critical-section state

## Verification
- Run: `./tools/configure.sh ea3131:nsh && make`
