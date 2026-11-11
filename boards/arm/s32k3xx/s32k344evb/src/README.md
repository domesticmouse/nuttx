# `s32k344evb/src` Component (`boards/arm/s32k3xx/s32k344evb/src`)

## Overview
Board-level C implementation (`src`) for `s32k344evb` (`arm/s32k3xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 10 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[s32k344evb.h:s32k3xx_bringup]` Public declaration `s32k3xx_bringup()`
- `[s32k344evb.h:s32k3xx_i2cdev_initialize]` Public declaration `s32k3xx_i2cdev_initialize()`
- `[s32k344evb.h:s32k3xx_spidev_initialize]` Public declaration `s32k3xx_spidev_initialize()`
- `[s32k344evb.h:GPIO_LED0_R]` Hardware/board configuration macros (`GPIO_LED0_R`, `GPIO_LED0_G`, `GPIO_LED0_B`, `GPIO_LED1_R`, `GPIO_LED1_G`, `GPIO_LED1_B` (+2 more))
- `[s32k3xx_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[s32k3xx_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[s32k3xx_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[s32k3xx_boot.c:s32k3xx_board_initialize]` Public function `s32k3xx_board_initialize()`
- `[s32k3xx_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[s32k3xx_bringup.c:s32k3xx_bringup]` Public function `s32k3xx_bringup()`
- `[s32k3xx_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[s32k3xx_buttons.c:board_buttons]` Public function `board_buttons()`
- `[s32k3xx_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[s32k3xx_clockconfig.c:g_initial_clkconfig]` Exported global symbol `g_initial_clkconfig`
- `[s32k3xx_i2c.c:s32k3xx_i2cdev_initialize]` Public function `s32k3xx_i2cdev_initialize()`
- `[s32k3xx_periphclocks.c:g_peripheral_clockconfig0]` Exported global symbol `g_peripheral_clockconfig0`
- `[s32k3xx_spi.c:s32k3xx_spidev_initialize]` Public function `s32k3xx_spidev_initialize()`
- `[s32k3xx_spi.c:s32k3xx_lpspi0select]` Public function `s32k3xx_lpspi0select()`
- `[s32k3xx_spi.c:s32k3xx_lpspi0status]` Public function `s32k3xx_lpspi0status()`
- `[s32k3xx_spi.c:s32k3xx_lpspi1select]` Public function `s32k3xx_lpspi1select()`
- `[s32k3xx_spi.c:s32k3xx_lpspi1status]` Public function `s32k3xx_lpspi1status()`
- `[s32k3xx_spi.c:s32k3xx_lpspi2select]` Public function `s32k3xx_lpspi2select()`
- `[s32k3xx_spi.c:s32k3xx_lpspi2status]` Public function `s32k3xx_lpspi2status()`
- *(+9 additional symbols across 10 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_S32K3XX_LPI2C`, `CONFIG_S32K3XX_LPSPI`
- `[s32k3xx_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[s32k3xx_i2c.c:s32k3xx_i2cdev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[s32k3xx_spi.c:s32k3xx_spidev_initialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[s32k3xx_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[s32k3xx_boot.c:s32k3xx_board_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[s32k3xx_bringup.c:s32k3xx_bringup]` Initializes/registers kernel devices or filesystems (`btn_lower_initialize()`, `nx_mount()`, `s32k3xx_i2cdev_initialize()`, `s32k3xx_spidev_initialize()`, `userled_lower_initialize()`)
- `[s32k3xx_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[s32k3xx_i2c.c:s32k3xx_i2cdev_initialize]` Initializes/registers kernel devices or filesystems (`i2c_register()`, `s32k3xx_i2cbus_initialize()`)
- `[s32k3xx_spi.c:s32k3xx_spidev_initialize]` Configures or drives hardware GPIO pins
- `[s32k3xx_spi.c:s32k3xx_spidev_initialize]` Initializes/registers kernel devices or filesystems (`fs26_initialize()`, `s32k3xx_lpspibus_initialize()`, `spi_register()`)
- `[s32k3xx_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh s32k344evb:nsh && make`
