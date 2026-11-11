# `stm32h747i-disco/src` Component (`boards/arm/stm32h7/stm32h747i-disco/src`)

## Overview
Board-level C implementation (`src`) for `stm32h747i-disco` (`arm/stm32h7`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 12 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[stm32h747i-disco.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[stm32h747i-disco.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[stm32h747i-disco.h:stm32_adc_setup]` Public declaration `stm32_adc_setup()`
- `[stm32h747i-disco.h:stm32_dma_alloc_init]` Public declaration `stm32_dma_alloc_init()`
- `[stm32h747i-disco.h:stm32_sdio_initialize]` Public declaration `stm32_sdio_initialize()`
- `[stm32h747i-disco.h:STM32_PROCFS_MOUNTPOINT]` Hardware/board configuration macros (`STM32_PROCFS_MOUNTPOINT`, `HAVE_RTC_DRIVER`, `GPIO_LD1`, `GPIO_LD2`, `GPIO_LD3`, `GPIO_LD4` (+10 more))
- `[stm32_adc.c:stm32_adc_setup]` Public function `stm32_adc_setup()`
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- `[stm32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[stm32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[stm32_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[stm32_dma_alloc.c:stm32_dma_alloc_init]` Public function `stm32_dma_alloc_init()`
- `[stm32_dma_alloc.c:fat_dma_alloc]` Public function `fat_dma_alloc()`
- `[stm32_dma_alloc.c:fat_dma_free]` Public function `fat_dma_free()`
- `[stm32_sdmmc.c:stm32_sdio_initialize]` Public function `stm32_sdio_initialize()`
- `[stm32_spi.c:stm32_spidev_initialize]` Public function `stm32_spidev_initialize()`
- `[stm32_spi.c:stm32_spi1select]` Public function `stm32_spi1select()`
- `[stm32_spi.c:stm32_spi1status]` Public function `stm32_spi1status()`
- *(+24 additional symbols across 12 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ADC`, `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_BOARDCTL_UNIQUEID`, `CONFIG_FAT_DMAMEMORY` (+3 more)
- `[stm32_adc.c:stm32_adc_setup]` Validates preconditions and returns `-ENODEV`, `-ENOSYS` on failure
- `[stm32_bringup.c:stm32_bringup]` Validates preconditions and returns `-ENOMEM` on failure
- `[stm32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[stm32_dma_alloc.c:#error]` Compile-time guard: `microSD DMA support requires CONFIG_GRAN`
- `[stm32_sdmmc.c:stm32_sdio_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_spi.c:stm32_spidev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_uid.c:board_uniqueid]` Validates preconditions and returns `-EINVAL` on failure
- `[stm32_usb.c:DEBUGASSERT]` Requires `iface == 0`

## Side Effects
- `[stm32_adc.c:stm32_adc_setup]` Configures or drives hardware GPIO pins
- `[stm32_adc.c:stm32_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`, `stm32_adc_initialize()`)
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `stm32_spidev_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`btn_lower_initialize()`, `i2c_register()`, `nx_mount()`, `rtc_initialize()`, `stm32_i2c_register()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_dma_alloc.c:stm32_dma_alloc_init]` Initializes/registers kernel devices or filesystems (`gran_initialize()`)
- `[stm32_sdmmc.c:stm32_sdio_initialize]` Configures or drives hardware GPIO pins
- `[stm32_sdmmc.c:stm32_sdio_initialize]` Initializes/registers kernel devices or filesystems (`sdio_initialize()`)
- `[stm32_usb.c:stm32_usbinitialize]` Configures or drives hardware GPIO pins
- `[stm32_usb.c:stm32_usbinitialize]` Initializes/registers kernel devices or filesystems (`stm32_otghshost_initialize()`, `usbhost_cdcacm_initialize()`, `usbhost_hub_initialize()`, `usbhost_msc_initialize()`)
- `[stm32_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh stm32h747i-disco:nsh && make`
