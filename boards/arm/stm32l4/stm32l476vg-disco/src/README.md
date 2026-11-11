# `stm32l476vg-disco/src` Component (`boards/arm/stm32l4/stm32l476vg-disco/src`)

## Overview
Board-level C implementation (`src`) for `stm32l476vg-disco` (`arm/stm32l4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 13 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[stm32l476vg-disco.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[stm32l476vg-disco.h:stm32_spiinitialize]` Public declaration `stm32_spiinitialize()`
- `[stm32l476vg-disco.h:stm32_usbinitialize]` Public declaration `stm32_usbinitialize()`
- `[stm32l476vg-disco.h:HAVE_PROC]` Hardware/board configuration macros (`HAVE_PROC`, `HAVE_RTC_DRIVER`, `HAVE_N25QXXX`, `HAVE_N25QXXX_NXFFS`, `HAVE_N25QXXX_SMARTFS`, `HAVE_N25QXXX_CHARDEV` (+24 more))
- `[etc_romfs.c:romfs_img]` Module symbol `romfs_img`
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_boot.c:stm32_board_initialize]` Public function `stm32_board_initialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- `[stm32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[stm32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[stm32_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[stm32_clockconfig.c:stm32_board_clockconfig]` Public function `stm32_board_clockconfig()`
- `[stm32_ioctl.c:board_ioctl]` Public function `board_ioctl()`
- `[stm32_netinit.c:arm_netinitialize]` Public function `arm_netinitialize()`
- `[stm32_spi.c:stm32_spiinitialize]` Public function `stm32_spiinitialize()`
- `[stm32_spi.c:stm32_spi1select]` Public function `stm32_spi1select()`
- `[stm32_spi.c:stm32_spi1status]` Public function `stm32_spi1status()`
- `[stm32_spi.c:stm32_spi2select]` Public function `stm32_spi2select()`
- `[stm32_spi.c:stm32_spi2status]` Public function `stm32_spi2status()`
- `[stm32_spi.c:stm32_spi3select]` Public function `stm32_spi3select()`
- *(+14 additional symbols across 13 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ADC`, `CONFIG_ARCH`, `CONFIG_ARCH_BOARD_STM32_CUSTOM_CLOCKCONFIG`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_BOARDCTL_IOCTL` (+5 more)
- `[stm32_bringup.c:stm32_bringup]` Validates preconditions and returns `-ENOMEM` on failure
- `[stm32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[stm32_ioctl.c:board_ioctl]` Validates preconditions and returns `-ENOTTY` on failure
- `[stm32_uid.c:board_uniqueid]` Validates preconditions and returns `-EINVAL` on failure
- `[stm32_usb.c:DEBUGASSERT]` Requires `iface == 0`
- `[stm32_userleds.c:DEBUGASSERT]` Requires `ret == OK`

## Side Effects
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_board_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`n25qxxx_initialize()`, `nx_mount()`, `nxffs_initialize()`, `rtc_initialize()`, `smart_initialize()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_clockconfig.c:stm32_board_clockconfig]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[stm32_spi.c:stm32_spiinitialize]` Configures or drives hardware GPIO pins
- `[stm32_usb.c:stm32_usbinitialize]` Configures or drives hardware GPIO pins
- `[stm32_usb.c:stm32_usbinitialize]` Initializes/registers kernel devices or filesystems (`stm32_otgfshost_initialize()`, `usbhost_cdcacm_initialize()`, `usbhost_hub_initialize()`, `usbhost_msc_initialize()`)
- `[stm32_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_userleds.c:board_userled_initialize]` Initializes/registers kernel devices or filesystems (`pm_register()`)

## Verification
- Run: `./tools/configure.sh stm32l476vg-disco:nsh && make`
