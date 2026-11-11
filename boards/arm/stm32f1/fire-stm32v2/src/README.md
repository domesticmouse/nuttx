# `fire-stm32v2/src` Component (`boards/arm/stm32f1/fire-stm32v2/src`)

## Overview
Board-level C implementation (`src`) for `fire-stm32v2` (`arm/stm32f1`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 12 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[fire-stm32v2.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[fire-stm32v2.h:stm32_usbinitialize]` Public declaration `stm32_usbinitialize()`
- `[fire-stm32v2.h:stm32_selectlcd]` Public declaration `stm32_selectlcd()`
- `[fire-stm32v2.h:stm32_sdinitialize]` Public declaration `stm32_sdinitialize()`
- `[fire-stm32v2.h:stm32_w25initialize]` Public declaration `stm32_w25initialize()`
- `[fire-stm32v2.h:HAVE_I2CTOOL]` Hardware/board configuration macros (`HAVE_I2CTOOL`, `GPIO_LCD_BACKLIGHT`, `GPIO_LED1`, `GPIO_LED2`, `GPIO_LED3`, `MIN_IRQBUTTON` (+9 more))
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_autoleds.c:up_ledpminitialize]` Public function `up_ledpminitialize()`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[stm32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[stm32_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[stm32_enc28j60.c:arm_netinitialize]` Public function `arm_netinitialize()`
- `[stm32_mmcsd.c:stm32_sdinitialize]` Public function `stm32_sdinitialize()`
- `[stm32_selectlcd.c:stm32_selectlcd]` Public function `stm32_selectlcd()`
- `[stm32_spi.c:stm32_spidev_initialize]` Public function `stm32_spidev_initialize()`
- `[stm32_spi.c:stm32_spi1select]` Public function `stm32_spi1select()`
- `[stm32_spi.c:stm32_spi1status]` Public function `stm32_spi1status()`
- `[stm32_spi.c:stm32_spi2select]` Public function `stm32_spi2select()`
- `[stm32_spi.c:stm32_spi2status]` Public function `stm32_spi2status()`
- *(+8 additional symbols across 12 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_ENC28J60`, `CONFIG_MTD_W25`, `CONFIG_STM32_FSMC` (+1 more)
- `[stm32_boot.c:#error]` Compile-time guard: `Only one MMC/SD slot: Slot 0`
- `[stm32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[stm32_enc28j60.c:DEBUGASSERT]` Requires `priv->handler`
- `[stm32_enc28j60.c:#error]` Compile-time guard: `Need CONFIG_STM32_SPI1 in the configuration`
- `[stm32_mmcsd.c:stm32_sdinitialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_selectlcd.c:#error]` Compile-time guard: `Required GPIO ports not enabled`
- `[stm32_w25.c:stm32_w25initialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_autoleds.c:board_autoled_initialize]` Initializes/registers kernel devices or filesystems (`pm_register()`)
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `i2c_register()`, `stm32_i2c_register()`, `stm32_i2cbus_initialize()`, `stm32_spidev_initialize()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_enc28j60.c:arm_netinitialize]` Configures or drives hardware GPIO pins
- `[stm32_enc28j60.c:arm_netinitialize]` Initializes/registers kernel devices or filesystems (`enc_initialize()`, `stm32_spibus_initialize()`)
- `[stm32_mmcsd.c:stm32_sdinitialize]` Initializes/registers kernel devices or filesystems (`sdio_initialize()`)
- `[stm32_selectlcd.c:stm32_selectlcd]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[stm32_selectlcd.c:stm32_selectlcd]` Configures or drives hardware GPIO pins
- `[stm32_selectlcd.c:stm32_selectlcd]` Modifies interrupt controller or critical-section state
- `[stm32_spi.c:stm32_spidev_initialize]` Configures or drives hardware GPIO pins
- `[stm32_usbdev.c:stm32_usbinitialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh fire-stm32v2:nsh && make`
