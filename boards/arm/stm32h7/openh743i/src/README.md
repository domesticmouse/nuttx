# `openh743i/src` Component (`boards/arm/stm32h7/openh743i/src`)

## Overview
Board-level C implementation (`src`) for `openh743i` (`arm/stm32h7`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[openh743i.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[openh743i.h:stm32_sdio_initialize]` Public declaration `stm32_sdio_initialize()`
- `[openh743i.h:stm32_usbinitialize]` Public declaration `stm32_usbinitialize()`
- `[openh743i.h:stm32_usbhost_initialize]` Public declaration `stm32_usbhost_initialize()`
- `[openh743i.h:STM32_PROCFS_MOUNTPOINT]` Hardware/board configuration macros (`STM32_PROCFS_MOUNTPOINT`, `GPIO_SDIO_NCD`, `SDIO_SLOTNO`, `SDIO_MINOR`, `GPIO_ULPI_RESET`, `GPIO_OTGFS_VBUS` (+2 more))
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- `[stm32_composite.c:board_composite_initialize]` Public function `board_composite_initialize()`
- `[stm32_composite.c:board_composite_connect]` Public function `board_composite_connect()`
- `[stm32_sdmmc.c:stm32_sdio_initialize]` Public function `stm32_sdio_initialize()`
- `[stm32_usb.c:stm32_usbinitialize]` Public function `stm32_usbinitialize()`
- `[stm32_usb.c:stm32_usbhost_initialize]` Public function `stm32_usbhost_initialize()`
- `[stm32_usb.c:stm32_usbhost_vbusdrive]` Public function `stm32_usbhost_vbusdrive()`
- `[stm32_usb.c:stm32_setup_overcurrent]` Public function `stm32_setup_overcurrent()`
- `[stm32_usb.c:stm32_usbsuspend]` Public function `stm32_usbsuspend()`
- `[stm32_usb.c:stm32_usbulpireset]` Public function `stm32_usbulpireset()`
- `[stm32_usbmsc.c:board_usbmsc_initialize]` Public function `board_usbmsc_initialize()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_STM32_SDMMC`, `CONFIG_USBDEV`, `CONFIG_USBDEV_COMPOSITE`, `CONFIG_USBHOST`, `CONFIG_USBMSC`
- `[stm32_composite.c:DEBUGASSERT]` Requires `g_mschandle == NULL`
- `[stm32_composite.c:DEBUGASSERT]` Requires `epin < STM32_NENDPOINTS`
- `[stm32_composite.c:DEBUGASSERT]` Requires `epout < STM32_NENDPOINTS`
- `[stm32_sdmmc.c:#error]` Compile-time guard: `SDMMC1 supported only`
- `[stm32_sdmmc.c:#error]` Compile-time guard: `SDMMC1 with IDMA does not work CONFIG_MM_REGIONS > 1`
- `[stm32_usb.c:DEBUGASSERT]` Requires `iface == 0`
- `[stm32_usb.c:#error]` Compile-time guard: `PWRON must be disabled for this configuration`
- `[stm32_usbmsc.c:#error]` Compile-time guard: `USBMSC high-speed require custom TXFIFO configuration that set EPIN FIFO...`

## Side Effects
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`nx_mount()`, `stm32_sdio_initialize()`, `stm32_usbhost_initialize()`, `usbdev_rndis_initialize()`)
- `[stm32_composite.c:board_composite_initialize]` Initializes/registers kernel devices or filesystems (`composite_initialize()`, `stm32_sdio_initialize()`)
- `[stm32_sdmmc.c:stm32_sdio_initialize]` Configures or drives hardware GPIO pins
- `[stm32_sdmmc.c:stm32_sdio_initialize]` Initializes/registers kernel devices or filesystems (`sdio_initialize()`)
- `[stm32_usb.c:stm32_usbinitialize]` Configures or drives hardware GPIO pins
- `[stm32_usb.c:stm32_usbinitialize]` Initializes/registers kernel devices or filesystems (`stm32_otgfshost_initialize()`, `usbhost_cdcacm_initialize()`, `usbhost_hub_initialize()`, `usbhost_msc_initialize()`)
- `[stm32_usbmsc.c:board_usbmsc_initialize]` Initializes/registers kernel devices or filesystems (`stm32_sdio_initialize()`)

## Verification
- Run: `./tools/configure.sh openh743i:nsh && make`
