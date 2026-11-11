# `flipperzero/src` Component (`boards/arm/stm32wb/flipperzero/src`)

## Overview
Board-level C implementation (`src`) for `flipperzero` (`arm/stm32wb`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[flipperzero.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[flipperzero.h:HAVE_PROC]` Hardware/board configuration macros (`HAVE_PROC`, `HAVE_RTC_DRIVER`, `GPIO_BTN_UP`, `GPIO_BTN_DOWN`, `GPIO_BTN_LEFT`, `GPIO_BTN_RIGH` (+1 more))
- `[stm32_boot.c:stm32_board_initialize]` Public function `stm32_board_initialize()`
- `[stm32_boot.c:arm_netinitialize]` Public function `arm_netinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_boot.c:board_ioctl]` Public function `board_ioctl()`
- `[stm32_boot.c:board_uniqueid]` Public function `board_uniqueid()`
- `[stm32_lcd_st7565.c:board_lcd_initialize]` Public function `board_lcd_initialize()`
- `[stm32_lcd_st7565.c:board_lcd_getdev]` Public function `board_lcd_getdev()`
- `[stm32_lcd_st7565.c:board_lcd_uninitialize]` Public function `board_lcd_uninitialize()`
- `[stm32_spi.c:stm32_spidev_initialize]` Public function `stm32_spidev_initialize()`
- `[stm32_spi.c:stm32_spi2select]` Public function `stm32_spi2select()`
- `[stm32_spi.c:stm32_spi2status]` Public function `stm32_spi2status()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_LCD_ST7565`, `CONFIG_SPI`
- `[stm32_boot.c:stm32_board_initialize]` Validates preconditions and returns `-EINVAL`, `-ENOTTY` on failure
- `[stm32_lcd_st7565.c:board_lcd_initialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[stm32_boot.c:stm32_board_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `board_lcd_initialize()`, `nx_mount()`, `rtc_initialize()`, `stm32_blehci_initialize()`)
- `[stm32_lcd_st7565.c:board_lcd_initialize]` Configures or drives hardware GPIO pins
- `[stm32_lcd_st7565.c:board_lcd_initialize]` Initializes/registers kernel devices or filesystems (`st7565_initialize()`, `stm32_spibus_initialize()`)
- `[stm32_spi.c:stm32_spidev_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh flipperzero:nsh && make`
