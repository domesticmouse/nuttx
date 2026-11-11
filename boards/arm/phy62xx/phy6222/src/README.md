# `phy6222/src` Component (`boards/arm/phy62xx/phy6222/src`)

## Overview
Board-level C implementation (`src`) for `phy6222` (`arm/phy62xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[phy6222.h:phy62xx_bringup]` Public declaration `phy62xx_bringup()`
- `[phy6222.h:GPIO_LED1]` Hardware/board configuration macros (`GPIO_LED1`, `GPIO_LED2`, `MIN_IRQBUTTON`, `MAX_IRQBUTTON`, `NUM_IRQBUTTONS`, `GPIO_BTN_USER`)
- `[boot.c:phy62xx_boardinitialize]` Public function `phy62xx_boardinitialize()`
- `[boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[bringup.c:phyplus_timer_initialize]` Public function `phyplus_timer_initialize()`
- `[bringup.c:phy62xx_bringup]` Public function `phy62xx_bringup()`
- `[buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[buttons.c:board_buttons]` Public function `board_buttons()`
- `[buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[etc_romfs.c:romfs_img]` Module symbol `romfs_img`
- `[reset.c:board_reset]` Public function `board_reset()`
- `[userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[userleds.c:board_userled]` Public function `board_userled()`
- `[userleds.c:board_userled_all]` Public function `board_userled_all()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ETC_ROMFS`

## Side Effects
- `[boot.c:phy62xx_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[bringup.c:phyplus_timer_initialize]` Initializes/registers kernel devices or filesystems (`nx_mount()`, `nxffs_initialize()`, `phyplus_wdt_initialize()`, `pplus_ble_initialize()`, `pplus_fls_initialize()`)

## Verification
- Run: `./tools/configure.sh phy6222:nsh && make`
