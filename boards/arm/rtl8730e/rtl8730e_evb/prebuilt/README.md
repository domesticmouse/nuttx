# `rtl8730e_evb/prebuilt` Component (`boards/arm/rtl8730e/rtl8730e_evb/prebuilt`)

## Overview
Board support prebuilt configuration header (`platform_autoconf.h`) for the Realtek `rtl8730e_evb` (`arm/rtl8730e`) evaluation board, defining vendor SDK autoconf macros for Cortex-A32 (`CONFIG_AMEBASMART`, `CONFIG_ARM_CORE_CA32`), flash VFS offsets, and Wi-Fi host controller (WHC) integration.

## Interface
- `[platform_autoconf.h:CONFIG_AMEBASMART]` Realtek AmebaSmart SDK platform configuration macros (`CONFIG_AMEBASMART`, `CONFIG_ARM_CORE_CA32`, `CONFIG_FLASH_VFS1_OFFSET`, `CONFIG_FLASH_VFS1_SIZE`, `CONFIG_WHC_WIFI_API_PATH`, `CONFIG_WHC_HOST`, `CONFIG_WHC_INTF_IPC`, `CONFIG_WLAN`, `CONFIG_LWIP_LAYER`)

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh rtl8730e_evb:nsh && make`
