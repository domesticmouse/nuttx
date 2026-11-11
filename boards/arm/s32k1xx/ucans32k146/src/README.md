# `ucans32k146/src` Component (`boards/arm/s32k1xx/ucans32k146/src`)

## Overview
Board-level C implementation (`src`) for `ucans32k146` (`arm/s32k1xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 11 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[ucans32k146.h:s32k1xx_bringup]` Public declaration `s32k1xx_bringup()`
- `[ucans32k146.h:s32k1xx_i2cdev_initialize]` Public declaration `s32k1xx_i2cdev_initialize()`
- `[ucans32k146.h:s32k1xx_spidev_initialize]` Public declaration `s32k1xx_spidev_initialize()`
- `[ucans32k146.h:s32k1xx_se05x_initialize]` Public declaration `s32k1xx_se05x_initialize()`
- `[ucans32k146.h:GPIO_LED_R]` Hardware/board configuration macros (`GPIO_LED_R`, `GPIO_LED_G`, `GPIO_LED_B`, `GPIO_SW3`, `GPIO_SE050_EN`)
- `[s32k1xx_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[s32k1xx_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[s32k1xx_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[s32k1xx_boot.c:s32k1xx_board_initialize]` Public function `s32k1xx_board_initialize()`
- `[s32k1xx_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[s32k1xx_bringup.c:s32k1xx_bringup]` Public function `s32k1xx_bringup()`
- `[s32k1xx_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[s32k1xx_buttons.c:board_buttons]` Public function `board_buttons()`
- `[s32k1xx_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[s32k1xx_clockconfig.c:g_initial_clkconfig]` Exported global symbol `g_initial_clkconfig`
- `[s32k1xx_i2c.c:s32k1xx_i2cdev_initialize]` Public function `s32k1xx_i2cdev_initialize()`
- `[s32k1xx_periphclocks.c:g_peripheral_clockconfig0]` Exported global symbol `g_peripheral_clockconfig0`
- `[s32k1xx_se05x.c:s32k1xx_se05x_initialize]` Public function `s32k1xx_se05x_initialize()`
- `[s32k1xx_spi.c:s32k1xx_spidev_initialize]` Public function `s32k1xx_spidev_initialize()`
- `[s32k1xx_spi.c:s32k1xx_lpspi0select]` Public function `s32k1xx_lpspi0select()`
- `[s32k1xx_spi.c:s32k1xx_lpspi0status]` Public function `s32k1xx_lpspi0status()`
- `[s32k1xx_spi.c:s32k1xx_lpspi1select]` Public function `s32k1xx_lpspi1select()`
- `[s32k1xx_spi.c:s32k1xx_lpspi1status]` Public function `s32k1xx_lpspi1status()`
- *(+6 additional symbols across 11 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_DEV_SE05X`, `CONFIG_I2C_DRIVER`, `CONFIG_S32K1XX_LPSPI`
- `[s32k1xx_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[s32k1xx_i2c.c:s32k1xx_i2cdev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[s32k1xx_se05x.c:s32k1xx_se05x_initialize]` Validates preconditions and returns `-EPERM` on failure
- `[s32k1xx_spi.c:s32k1xx_spidev_initialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[s32k1xx_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[s32k1xx_boot.c:s32k1xx_board_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[s32k1xx_bringup.c:s32k1xx_bringup]` Configures or drives hardware GPIO pins
- `[s32k1xx_bringup.c:s32k1xx_bringup]` Initializes/registers kernel devices or filesystems (`btn_lower_initialize()`, `nx_mount()`, `progmem_initialize()`, `s32k1xx_eeeprom_register()`, `s32k1xx_i2cdev_initialize()`)
- `[s32k1xx_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[s32k1xx_i2c.c:s32k1xx_i2cdev_initialize]` Initializes/registers kernel devices or filesystems (`i2c_register()`, `s32k1xx_flexio_i2cbus_initialize()`, `s32k1xx_i2cbus_initialize()`)
- `[s32k1xx_se05x.c:s32k1xx_se05x_initialize]` Configures or drives hardware GPIO pins
- `[s32k1xx_se05x.c:s32k1xx_se05x_initialize]` Initializes/registers kernel devices or filesystems (`s32k1xx_i2cbus_initialize()`, `se05x_register()`)
- `[s32k1xx_spi.c:s32k1xx_spidev_initialize]` Configures or drives hardware GPIO pins
- `[s32k1xx_spi.c:s32k1xx_spidev_initialize]` Initializes/registers kernel devices or filesystems (`s32k1xx_lpspibus_initialize()`, `spi_register()`)
- `[s32k1xx_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh ucans32k146:nsh && make`
