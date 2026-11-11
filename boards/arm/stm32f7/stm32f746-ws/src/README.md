# `stm32f746-ws/src` Component (`boards/arm/stm32f7/stm32f746-ws/src`)

## Overview
Board-level C implementation (`src`) for `stm32f746-ws` (`arm/stm32f7`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 6 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[stm32f746-ws.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[stm32f746-ws.h:stm32_sdio_initialize]` Public declaration `stm32_sdio_initialize()`
- `[stm32f746-ws.h:stm32_dma_alloc_init]` Public declaration `stm32_dma_alloc_init()`
- `[stm32f746-ws.h:STM32_PROCFS_MOUNTPOINT]` Hardware/board configuration macros (`STM32_PROCFS_MOUNTPOINT`, `GPIO_LD1`, `GPIO_LD2`, `GPIO_LD3`, `LED_DRIVER_PATH`, `GPIO_BTN_USER` (+3 more))
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_dma_alloc.c:stm32_dma_alloc_init]` Public function `stm32_dma_alloc_init()`
- `[stm32_dma_alloc.c:fat_dma_alloc]` Public function `fat_dma_alloc()`
- `[stm32_dma_alloc.c:fat_dma_free]` Public function `fat_dma_free()`
- `[stm32_sdmmc.c:stm32_sdio_initialize]` Public function `stm32_sdio_initialize()`
- `[stm32_spi.c:stm32_spidev_initialize]` Public function `stm32_spidev_initialize()`
- `[stm32_spi.c:stm32_spi1select]` Public function `stm32_spi1select()`
- `[stm32_spi.c:stm32_spi1status]` Public function `stm32_spi1status()`
- `[stm32_spi.c:stm32_spi2select]` Public function `stm32_spi2select()`
- `[stm32_spi.c:stm32_spi2status]` Public function `stm32_spi2status()`
- `[stm32_spi.c:stm32_spi3select]` Public function `stm32_spi3select()`
- `[stm32_spi.c:stm32_spi3status]` Public function `stm32_spi3status()`
- `[stm32_spi.c:stm32_spi4select]` Public function `stm32_spi4select()`
- `[stm32_spi.c:stm32_spi4status]` Public function `stm32_spi4status()`
- `[stm32_spi.c:stm32_spi5select]` Public function `stm32_spi5select()`
- `[stm32_spi.c:stm32_spi5status]` Public function `stm32_spi5status()`
- `[stm32_spi.c:stm32_spi6select]` Public function `stm32_spi6select()`
- `[stm32_spi.c:stm32_spi6status]` Public function `stm32_spi6status()`
- *(+11 additional symbols across 6 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_STM32_OTGFS`, `CONFIG_STM32_SDMMC1`
- `[stm32_dma_alloc.c:#error]` Compile-time guard: `microSD DMA support requires CONFIG_GRAN`
- `[stm32_sdmmc.c:stm32_sdio_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_spi.c:stm32_spidev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_usb.c:DEBUGASSERT]` Requires `iface == 0`

## Side Effects
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`i2c_register()`, `stm32_i2c_register()`, `stm32_i2cbus_initialize()`, `stm32_sdio_initialize()`, `stm32_spidev_initialize()`)
- `[stm32_dma_alloc.c:stm32_dma_alloc_init]` Initializes/registers kernel devices or filesystems (`gran_initialize()`)
- `[stm32_sdmmc.c:stm32_sdio_initialize]` Configures or drives hardware GPIO pins
- `[stm32_sdmmc.c:stm32_sdio_initialize]` Initializes/registers kernel devices or filesystems (`sdio_initialize()`)
- `[stm32_usb.c:stm32_usbinitialize]` Configures or drives hardware GPIO pins
- `[stm32_usb.c:stm32_usbinitialize]` Initializes/registers kernel devices or filesystems (`stm32_otgfshost_initialize()`, `usbhost_cdcacm_initialize()`, `usbhost_hub_initialize()`, `usbhost_msc_initialize()`)

## Verification
- Run: `./tools/configure.sh stm32f746-ws:nsh && make`
