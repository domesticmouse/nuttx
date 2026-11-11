# `ci20/src` Component (`boards/mips/jz4780/ci20/src`)

## Overview
Board-level C implementation (`src`) for `ci20` (`mips/jz4780`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[ci20.h:jz4780_led_initialize]` Public declaration `jz4780_led_initialize()`
- `[ci20.h:jz4780_bringup]` Public declaration `jz4780_bringup()`
- `[ci20.h:jz_dma_alloc_init]` Public declaration `jz_dma_alloc_init()`
- `[ci20_network.c:mips_netinitialize]` Public function `mips_netinitialize()`
- `[jz4780_boot.c:jz4780_boardinitialize]` Public function `jz4780_boardinitialize()`
- `[jz4780_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[jz4780_bringup.c:jz4780_bringup]` Public function `jz4780_bringup()`
- `[jz4780_usb.c:jz_usbhost_bootinitialize]` Public function `jz_usbhost_bootinitialize()`
- `[jz4780_usb.c:jz_usbhost_initialize]` Public function `jz_usbhost_initialize()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_USBHOST`
- `[jz4780_usb.c:jz_usbhost_bootinitialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[ci20_network.c:mips_netinitialize]` Configures or drives hardware GPIO pins
- `[ci20_network.c:mips_netinitialize]` Initializes/registers kernel devices or filesystems (`dm9x_initialize()`)
- `[jz4780_bringup.c:jz4780_bringup]` Configures or drives hardware GPIO pins
- `[jz4780_bringup.c:jz4780_bringup]` Initializes/registers kernel devices or filesystems (`fb_register()`, `jz_usbhost_initialize()`, `nx_mount()`)
- `[jz4780_usb.c:jz_usbhost_bootinitialize]` Initializes/registers kernel devices or filesystems (`jz_ehci_initialize()`, `jz_ohci_initialize()`, `usbhost_cdcacm_initialize()`, `usbhost_hub_initialize()`, `usbhost_msc_initialize()`)

## Verification
- Run: `./tools/configure.sh ci20:nsh && make`
