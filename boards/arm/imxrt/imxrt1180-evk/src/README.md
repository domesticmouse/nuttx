# `imxrt1180-evk/src` Component (`boards/arm/imxrt/imxrt1180-evk/src`)

## Overview
Board-level C implementation (`src`) for `imxrt1180-evk` (`arm/imxrt`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 10 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[imxrt1180-evk.h:imxrt_bringup]` Public declaration `imxrt_bringup()`
- `[imxrt1180-evk.h:imxrt_dma_alloc_init]` Public declaration `imxrt_dma_alloc_init()`
- `[imxrt_appinit.c:board_app_initialize]` Public function `board_app_initialize()`
- `[imxrt_boot.c:imxrt_boardinitialize]` Public function `imxrt_boardinitialize()`
- `[imxrt_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[imxrt_bootloader.c:bootloader_main]` Public function `bootloader_main()`
- `[imxrt_bringup.c:imxrt_bringup]` Public function `imxrt_bringup()`
- `[imxrt_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[imxrt_buttons.c:board_buttons]` Public function `board_buttons()`
- `[imxrt_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[imxrt_clockconfig_m33.c:g_initial_clkconfig]` Exported global symbol `g_initial_clkconfig`
- `[imxrt_clockconfig_m7.c:g_initial_clkconfig]` Exported global symbol `g_initial_clkconfig`
- `[imxrt_dma_alloc.c:imxrt_dma_alloc_init]` Public function `imxrt_dma_alloc_init()`
- `[imxrt_dma_alloc.c:usbdev_dma_alloc]` Public function `usbdev_dma_alloc()`
- `[imxrt_dma_alloc.c:usbdev_dma_free]` Public function `usbdev_dma_free()`
- `[imxrt_dma_alloc.c:fat_dma_alloc]` Public function `fat_dma_alloc()`
- `[imxrt_dma_alloc.c:fat_dma_free]` Public function `fat_dma_free()`
- `[imxrt_flash_headers.c:g_flash_config]` Exported global symbol `g_flash_config`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_CORTEXM33`, `CONFIG_FAT_DMAMEMORY`, `CONFIG_IMXRT1180_EVK_BOOTLOADER`, `CONFIG_IMXRT_TRDC`, `CONFIG_USBDEV_DMAMEMORY`
- `[imxrt_bringup.c:imxrt_bringup]` Validates preconditions and returns `-ENODEV` on failure
- `[imxrt_buttons.c:#error]` Compile-time guard: `CONFIG_ARCH_IRQBUTTONS requires CONFIG_IMXRT_GPIO_IRQ`
- `[imxrt_dma_alloc.c:DEBUGASSERT]` Requires `g_dma_allocator != NULL`

## Side Effects
- `[imxrt_bootloader.c:bootloader_main]` Modifies interrupt controller or critical-section state
- `[imxrt_bringup.c:imxrt_bringup]` Initializes/registers kernel devices or filesystems (`btn_lower_initialize()`, `imxrt_sdmmc_initialize()`, `imxrt_usdhc_initialize()`, `nx_mount()`)
- `[imxrt_dma_alloc.c:imxrt_dma_alloc_init]` Initializes/registers kernel devices or filesystems (`gran_initialize()`)

## Verification
- Run: `./tools/configure.sh imxrt1180-evk:nsh && make`
