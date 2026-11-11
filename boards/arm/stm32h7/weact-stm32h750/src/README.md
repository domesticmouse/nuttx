# `weact-stm32h750/src` Component (`boards/arm/stm32h7/weact-stm32h750/src`)

## Overview
Board-level C implementation (`src`) for `weact-stm32h750` (`arm/stm32h7`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 10 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[weact-stm32h750.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[weact-stm32h750.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[weact-stm32h750.h:stm32_dma_alloc_init]` Public declaration `stm32_dma_alloc_init()`
- `[weact-stm32h750.h:stm32_sdio_initialize]` Public declaration `stm32_sdio_initialize()`
- `[weact-stm32h750.h:HAVE_USBDEV]` Hardware/board configuration macros (`HAVE_USBDEV`, `HAVE_USBHOST`, `STM32_PROCFS_MOUNTPOINT`, `HAVE_RTC_DRIVER`, `GPIO_LD1`, `GPIO_BTN_USER` (+7 more))
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- `[stm32_dma_alloc.c:stm32_dma_alloc_init]` Public function `stm32_dma_alloc_init()`
- `[stm32_dma_alloc.c:fat_dma_alloc]` Public function `fat_dma_alloc()`
- `[stm32_dma_alloc.c:fat_dma_free]` Public function `fat_dma_free()`
- `[stm32_ioctl.c:board_ioctl]` Public function `board_ioctl()`
- `[stm32_lcd_st7735.c:board_lcd_initialize]` Public function `board_lcd_initialize()`
- `[stm32_lcd_st7735.c:board_lcd_getdev]` Public function `board_lcd_getdev()`
- `[stm32_lcd_st7735.c:board_lcd_uninitialize]` Public function `board_lcd_uninitialize()`
- `[stm32_sdmmc.c:stm32_sdio_initialize]` Public function `stm32_sdio_initialize()`
- `[stm32_spi.c:stm32_spidev_initialize]` Public function `stm32_spidev_initialize()`
- `[stm32_spi.c:stm32_spi4select]` Public function `stm32_spi4select()`
- `[stm32_spi.c:stm32_spi4status]` Public function `stm32_spi4status()`
- `[stm32_spi.c:stm32_spi4cmddata]` Public function `stm32_spi4cmddata()`
- *(+4 additional symbols across 10 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_LEDS`, `CONFIG_FAT_DMAMEMORY`, `CONFIG_LCD_ST7735`, `CONFIG_STM32_SDMMC`, `CONFIG_VIDEO_FB`
- `[stm32_dma_alloc.c:#error]` Compile-time guard: `microSD DMA support requires CONFIG_GRAN`
- `[stm32_ioctl.c:board_ioctl]` Validates preconditions and returns `-ENOTTY` on failure
- `[stm32_lcd_st7735.c:board_lcd_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_sdmmc.c:stm32_sdio_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_spi.c:stm32_spidev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_usb.c:DEBUGASSERT]` Requires `iface == 0`

## Side Effects
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `stm32_spidev_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`fb_register()`, `nx_mount()`, `stm32_sdio_initialize()`)
- `[stm32_dma_alloc.c:stm32_dma_alloc_init]` Initializes/registers kernel devices or filesystems (`gran_initialize()`)
- `[stm32_lcd_st7735.c:board_lcd_initialize]` Configures or drives hardware GPIO pins
- `[stm32_lcd_st7735.c:board_lcd_initialize]` Initializes/registers kernel devices or filesystems (`stm32_spibus_initialize()`)
- `[stm32_sdmmc.c:stm32_sdio_initialize]` Configures or drives hardware GPIO pins
- `[stm32_sdmmc.c:stm32_sdio_initialize]` Initializes/registers kernel devices or filesystems (`sdio_initialize()`)
- `[stm32_spi.c:stm32_spidev_initialize]` Configures or drives hardware GPIO pins
- `[stm32_usb.c:stm32_usbhost_initialize]` Configures or drives hardware GPIO pins
- `[stm32_usb.c:stm32_usbhost_initialize]` Initializes/registers kernel devices or filesystems (`stm32_otgfshost_initialize()`, `usbhost_cdcacm_initialize()`, `usbhost_hub_initialize()`, `usbhost_msc_initialize()`)

## Verification
- Run: `./tools/configure.sh weact-stm32h750:nsh && make`
