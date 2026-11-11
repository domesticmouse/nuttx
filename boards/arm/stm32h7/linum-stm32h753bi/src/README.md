# `linum-stm32h753bi/src` Component (`boards/arm/stm32h7/linum-stm32h753bi/src`)

## Overview
Board-level C implementation (`src`) for `linum-stm32h753bi` (`arm/stm32h7`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 16 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[linum-stm32h753bi.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[linum-stm32h753bi.h:stm32_usbinitialize]` Public declaration `stm32_usbinitialize()`
- `[linum-stm32h753bi.h:stm32_dma_alloc_init]` Public declaration `stm32_dma_alloc_init()`
- `[linum-stm32h753bi.h:stm32_sdio_initialize]` Public declaration `stm32_sdio_initialize()`
- `[linum-stm32h753bi.h:stm32_at24_init]` Public declaration `stm32_at24_init()`
- `[linum-stm32h753bi.h:stm32_pwm_setup]` Public declaration `stm32_pwm_setup()`
- `[linum-stm32h753bi.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[linum-stm32h753bi.h:stm32_w25qxxx_setup]` Public declaration `stm32_w25qxxx_setup()`
- `[linum-stm32h753bi.h:stm32_mfrc522initialize]` Public declaration `stm32_mfrc522initialize()`
- `[linum-stm32h753bi.h:stm32_tsc_setup]` Public declaration `stm32_tsc_setup()`
- `[linum-stm32h753bi.h:stm32_usbhost_initialize]` Public declaration `stm32_usbhost_initialize()`
- `[linum-stm32h753bi.h:GPIO_LD1]` Hardware/board configuration macros (`GPIO_LD1`, `GPIO_LD2`, `GPIO_LD3`, `GPIO_LED_RED`, `GPIO_LED_GREEN`, `GPIO_LED_BLUE` (+15 more))
- `[stm32_at24.c:stm32_at24_init]` Public function `stm32_at24_init()`
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- `[stm32_dma_alloc.c:stm32_dma_alloc_init]` Public function `stm32_dma_alloc_init()`
- `[stm32_dma_alloc.c:fat_dma_alloc]` Public function `fat_dma_alloc()`
- `[stm32_dma_alloc.c:fat_dma_free]` Public function `fat_dma_free()`
- `[stm32_lcd.c:up_fbinitialize]` Public function `up_fbinitialize()`
- *(+21 additional symbols across 16 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_LEDS`, `CONFIG_CL_MFRC522`, `CONFIG_FAT_DMAMEMORY`, `CONFIG_I2C_EE_24XX`, `CONFIG_INPUT_FT5X06` (+7 more)
- `[stm32_at24.c:stm32_at24_init]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_bringup.c:stm32_bringup]` Validates preconditions and returns `-ENOMEM` on failure
- `[stm32_dma_alloc.c:#error]` Compile-time guard: `microSD DMA support requires CONFIG_GRAN`
- `[stm32_mfrc522.c:stm32_mfrc522initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_pwm.c:stm32_pwm_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_sdmmc.c:stm32_sdio_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_spi.c:stm32_spidev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_touchscreen.c:DEBUGASSERT]` Requires `minor == CONFIG_FT5X06_DEVMINOR`
- `[stm32_touchscreen.c:#error]` Compile-time guard: `FT5x06 support requires CONFIG_INPUT`
- `[stm32_touchscreen.c:#error]` Compile-time guard: `FT5x06 support requires CONFIG_STM32_I2C3`
- `[stm32_usb.c:DEBUGASSERT]` Requires `iface == 0`

## Side Effects
- `[stm32_at24.c:stm32_at24_init]` Initializes/registers kernel devices or filesystems (`ee24xx_initialize()`, `stm32_i2cbus_initialize()`)
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Configures or drives hardware GPIO pins
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`board_qencoder_initialize()`, `board_tone_initialize()`, `fb_register()`, `i2c_register()`, `nx_mount()`)
- `[stm32_dma_alloc.c:stm32_dma_alloc_init]` Initializes/registers kernel devices or filesystems (`gran_initialize()`)
- `[stm32_lcd.c:up_fbinitialize]` Configures or drives hardware GPIO pins
- `[stm32_mfrc522.c:stm32_mfrc522initialize]` Initializes/registers kernel devices or filesystems (`mfrc522_register()`, `stm32_spibus_initialize()`)
- `[stm32_pwm.c:stm32_pwm_setup]` Initializes/registers kernel devices or filesystems (`pwm_register()`)
- `[stm32_sdmmc.c:stm32_sdio_initialize]` Configures or drives hardware GPIO pins
- `[stm32_sdmmc.c:stm32_sdio_initialize]` Initializes/registers kernel devices or filesystems (`sdio_initialize()`)
- `[stm32_spi.c:stm32_spidev_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh linum-stm32h753bi:nsh && make`
