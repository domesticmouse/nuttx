# `sam4e-ek/src` Component (`boards/arm/sam34/sam4e-ek/src`)

## Overview
Board-level C implementation (`src`) for `sam4e-ek` (`arm/sam34`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 13 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[sam4e-ek.h:sam_spidev_initialize]` Public declaration `sam_spidev_initialize()`
- `[sam4e-ek.h:sam_hsmci_initialize]` Public declaration `sam_hsmci_initialize()`
- `[sam4e-ek.h:sam_netinitialize]` Public declaration `sam_netinitialize()`
- `[sam4e-ek.h:sam_cardinserted]` Public declaration `sam_cardinserted()`
- `[sam4e-ek.h:sam_writeprotected]` Public declaration `sam_writeprotected()`
- `[sam4e-ek.h:sam_at25_automount]` Public declaration `sam_at25_automount()`
- `[sam4e-ek.h:sam_tsc_setup]` Public declaration `sam_tsc_setup()`
- `[sam4e-ek.h:HAVE_HSMCI]` Hardware/board configuration macros (`HAVE_HSMCI`, `HAVE_AT25`, `HAVE_USBDEV`, `HAVE_USBMONITOR`, `HAVE_NETWORK`, `GPIO_LCD_BKL` (+24 more))
- `[sam_ads7843e.c:sam_tsc_setup]` Public function `sam_tsc_setup()`
- `[sam_at25.c:sam_at25_automount]` Public function `sam_at25_automount()`
- `[sam_boot.c:sam_boardinitialize]` Public function `sam_boardinitialize()`
- `[sam_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[sam_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[sam_buttons.c:board_buttons]` Public function `board_buttons()`
- `[sam_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[sam_ethernet.c:sam_netinitialize]` Public function `sam_netinitialize()`
- `[sam_ethernet.c:arch_phy_irq]` Public function `arch_phy_irq()`
- `[sam_hsmci.c:sam_hsmci_initialize]` Public function `sam_hsmci_initialize()`
- `[sam_hsmci.c:sam_cardinserted]` Public function `sam_cardinserted()`
- `[sam_hsmci.c:sam_writeprotected]` Public function `sam_writeprotected()`
- `[sam_ili9325.c:board_lcd_initialize]` Public function `board_lcd_initialize()`
- `[sam_ili9325.c:board_lcd_getdev]` Public function `board_lcd_getdev()`
- `[sam_ili9325.c:board_lcd_uninitialize]` Public function `board_lcd_uninitialize()`
- *(+11 additional symbols across 13 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_INPUT_ADS7843E`, `CONFIG_LCD`, `CONFIG_MTD_AT25`, `CONFIG_SAM34_EMAC`, `CONFIG_SAM34_HSMCI`, `CONFIG_SAM34_SPI0` (+3 more)
- `[sam4e-ek.h:sam_spidev_initialize]` Validates preconditions and returns `-ENOSYS` on failure
- `[sam_ads7843e.c:DEBUGASSERT]` Requires `minor == 0`
- `[sam_ads7843e.c:#error]` Compile-time guard: `Touchscreen support requires CONFIG_SAM34_SPI0`
- `[sam_ads7843e.c:#error]` Compile-time guard: `Touchscreen support requires CONFIG_SAM34_GPIOA_IRQ`
- `[sam_at25.c:sam_at25_automount]` Validates preconditions and returns `-ENODEV` on failure
- `[sam_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[sam_ethernet.c:DEBUGASSERT]` Requires `intf`
- `[sam_hsmci.c:sam_hsmci_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[sam_ili9325.c:DEBUGASSERT]` Requires `power > 0 && power <= CONFIG_LCD_MAXPOWER`
- `[sam_ili9325.c:DEBUGASSERT]` Requires `buffer && ((uintptr_t)buffer & 1) == 0`
- `[sam_ili9325.c:DEBUGASSERT]` Requires `dev && vinfo`

## Side Effects
- `[sam_ads7843e.c:sam_tsc_setup]` Configures or drives hardware GPIO pins
- `[sam_ads7843e.c:sam_tsc_setup]` Initializes/registers kernel devices or filesystems (`ads7843e_register()`, `sam_spibus_initialize()`)
- `[sam_ads7843e.c:sam_tsc_setup]` Modifies interrupt controller or critical-section state
- `[sam_at25.c:sam_at25_automount]` Initializes/registers kernel devices or filesystems (`at25_initialize()`, `nx_mount()`, `nxffs_initialize()`, `sam_spibus_initialize()`)
- `[sam_boot.c:sam_boardinitialize]` Configures or drives hardware GPIO pins
- `[sam_boot.c:sam_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `sam_hsmci_initialize()`, `sam_spidev_initialize()`)
- `[sam_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[sam_buttons.c:board_button_initialize]` Modifies interrupt controller or critical-section state
- `[sam_ethernet.c:sam_netinitialize]` Configures or drives hardware GPIO pins
- `[sam_ethernet.c:sam_netinitialize]` Modifies interrupt controller or critical-section state
- `[sam_hsmci.c:sam_hsmci_initialize]` Configures or drives hardware GPIO pins
- `[sam_hsmci.c:sam_hsmci_initialize]` Initializes/registers kernel devices or filesystems (`sdio_initialize()`)

## Verification
- Run: `./tools/configure.sh sam4e-ek:nsh && make`
