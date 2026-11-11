# `gd32f450zk-aiotbox/src` Component (`boards/arm/gd32f4/gd32f450zk-aiotbox/src`)

## Overview
Board-level C implementation (`src`) for `gd32f450zk-aiotbox` (`arm/gd32f4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 12 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[gd32f450z_aiotbox.h:gd32_bringup]` Public declaration `gd32_bringup()`
- `[gd32f450z_aiotbox.h:gd32_spidev_initialize]` Public declaration `gd32_spidev_initialize()`
- `[gd32f450z_aiotbox.h:gd32_gpio_initialize]` Public declaration `gd32_gpio_initialize()`
- `[gd32f450z_aiotbox.h:gd32_dma_alloc_init]` Public declaration `gd32_dma_alloc_init()`
- `[gd32f450z_aiotbox.h:gd32_sdio_initialize]` Public declaration `gd32_sdio_initialize()`
- `[gd32f450z_aiotbox.h:gd32_i2c_initialize]` Public declaration `gd32_i2c_initialize()`
- `[gd32f450z_aiotbox.h:GD32_PROCFS_MOUNTPOINT]` Hardware/board configuration macros (`GD32_PROCFS_MOUNTPOINT`, `CONFIG_GD32F4_NXFFS_MOUNTPT`, `GPIO_LED1`, `GPIO_LED2`, `GPIO_LED3`, `LED1` (+15 more))
- `[gd32f4xx_romfs.h:gd32_romfs_initialize]` Public declaration `gd32_romfs_initialize()`
- `[gd32f4xx_romfs.h:ROMFS_SECTOR_SIZE]` Hardware/board configuration macros (`ROMFS_SECTOR_SIZE`)
- `[gd32f4xx_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[gd32f4xx_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[gd32f4xx_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[gd32f4xx_boot.c:gd32_boardinitialize]` Public function `gd32_boardinitialize()`
- `[gd32f4xx_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[gd32f4xx_bringup.c:gd32_bringup]` Public function `gd32_bringup()`
- `[gd32f4xx_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[gd32f4xx_buttons.c:board_buttons]` Public function `board_buttons()`
- `[gd32f4xx_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[gd32f4xx_gpio.c:gd32_gpio_initialize]` Public function `gd32_gpio_initialize()`
- `[gd32f4xx_i2c.c:gd32_i2c_initialize]` Public function `gd32_i2c_initialize()`
- `[gd32f4xx_romfs.c:gd32_romfs_initialize]` Public function `gd32_romfs_initialize()`
- `[gd32f4xx_sdio.c:gd32_sdio_initialize]` Public function `gd32_sdio_initialize()`
- `[gd32f4xx_spi.c:gd32_spidev_initialize]` Public function `gd32_spidev_initialize()`
- *(+21 additional symbols across 12 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_DEV_GPIO`, `CONFIG_I2C`, `CONFIG_MMCSD`, `CONFIG_SPI`
- `[gd32f4xx_gpio.c:DEBUGASSERT]` Requires `gd32gpio != NULL && value != NULL`
- `[gd32f4xx_gpio.c:DEBUGASSERT]` Requires `gd32gpio->id < BOARD_NGPIOIN`
- `[gd32f4xx_romfs.c:#error]` Compile-time guard: `CONFIG_GD32F4_ROMFS must be defined`
- `[gd32f4xx_romfs.c:#error]` Compile-time guard: `CONFIG_GD32F4_ROMFS_IMAGEFILE must be defined`
- `[gd32f4xx_sdio.c:gd32_sdio_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[gd32f4xx_spi.c:gd32_spidev_initialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[gd32f4xx_boot.c:gd32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `gd32_spidev_initialize()`)
- `[gd32f4xx_bringup.c:gd32_bringup]` Initializes/registers kernel devices or filesystems (`board_button_initialize()`, `btn_lower_initialize()`, `gd32_gpio_initialize()`, `gd32_i2c_initialize()`, `gd32_romfs_initialize()`)
- `[gd32f4xx_buttons.c:board_button_initialize]` Modifies interrupt controller or critical-section state
- `[gd32f4xx_gpio.c:gd32_gpio_initialize]` Initializes/registers kernel devices or filesystems (`gpio_pin_register()`)
- `[gd32f4xx_gpio.c:gd32_gpio_initialize]` Modifies interrupt controller or critical-section state
- `[gd32f4xx_i2c.c:gd32_i2c_initialize]` Initializes/registers kernel devices or filesystems (`gd32_i2cbus_initialize()`, `i2c_register()`)
- `[gd32f4xx_romfs.c:gd32_romfs_initialize]` Initializes/registers kernel devices or filesystems (`nx_mount()`, `romdisk_register()`)
- `[gd32f4xx_sdio.c:gd32_sdio_initialize]` Initializes/registers kernel devices or filesystems (`sdio_initialize()`)

## Verification
- Run: `./tools/configure.sh gd32f450zk-aiotbox:aiotboxnsh && make`
