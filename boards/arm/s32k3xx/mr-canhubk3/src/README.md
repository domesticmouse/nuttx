# `mr-canhubk3/src` Component (`boards/arm/s32k3xx/mr-canhubk3/src`)

## Overview
Board-level C implementation (`src`) for `mr-canhubk3` (`arm/s32k3xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 13 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[mr-canhubk3.h:s32k3xx_bringup]` Public declaration `s32k3xx_bringup()`
- `[mr-canhubk3.h:s32k3xx_i2cdev_initialize]` Public declaration `s32k3xx_i2cdev_initialize()`
- `[mr-canhubk3.h:s32k3xx_spidev_initialize]` Public declaration `s32k3xx_spidev_initialize()`
- `[mr-canhubk3.h:s32k3xx_tja1153_initialize]` Public declaration `s32k3xx_tja1153_initialize()`
- `[mr-canhubk3.h:s32k3xx_selftest]` Public declaration `s32k3xx_selftest()`
- `[mr-canhubk3.h:GPIO_LED_R]` Hardware/board configuration macros (`GPIO_LED_R`, `GPIO_LED_G`, `GPIO_LED_B`, `GPIO_SW1`, `GPIO_SW2`)
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
- `[s32k3xx_dma_alloc.c:s32k3xx_dma_alloc_init]` Public function `s32k3xx_dma_alloc_init()`
- `[s32k3xx_dma_alloc.c:fat_dma_alloc]` Public function `fat_dma_alloc()`
- `[s32k3xx_dma_alloc.c:fat_dma_free]` Public function `fat_dma_free()`
- `[s32k3xx_i2c.c:s32k3xx_i2cdev_initialize]` Public function `s32k3xx_i2cdev_initialize()`
- `[s32k3xx_periphclocks.c:g_peripheral_clockconfig0]` Exported global symbol `g_peripheral_clockconfig0`
- `[s32k3xx_selftest.c:s32k3xx_selftest]` Public function `s32k3xx_selftest()`
- `[s32k3xx_spi.c:s32k3xx_spidev_initialize]` Public function `s32k3xx_spidev_initialize()`
- *(+14 additional symbols across 13 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_FAT_DMAMEMORY`, `CONFIG_S32K3XX_FLEXCAN`, `CONFIG_S32K3XX_LPI2C`, `CONFIG_S32K3XX_LPSPI` (+1 more)
- `[s32k3xx_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[s32k3xx_dma_alloc.c:#error]` Compile-time guard: `microSD DMA support requires CONFIG_GRAN`
- `[s32k3xx_i2c.c:s32k3xx_i2cdev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[s32k3xx_selftest.c:#error]` Compile-time guard: `CONFIG_S32K3XX_LPI2C1 needs to be enabled to perform SE050 self-test`
- `[s32k3xx_selftest.c:#error]` Compile-time guard: `CONFIG_S32K3XX_FLEXCAN0-3 need to be enabled to perform CAN self-test`
- `[s32k3xx_spi.c:s32k3xx_spidev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[s32k3xx_tja1153.c:#error]` Compile-time guard: `FLEXCAN4_ARBI_BITRATE > 500000`
- `[s32k3xx_tja1153.c:#error]` Compile-time guard: `FLEXCAN4_BITRATE > 500000`

## Side Effects
- `[s32k3xx_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[s32k3xx_boot.c:s32k3xx_board_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[s32k3xx_bringup.c:s32k3xx_bringup]` Initializes/registers kernel devices or filesystems (`btn_lower_initialize()`, `mx25rxx_initialize()`, `nx_mount()`, `nxffs_initialize()`, `progmem_initialize()`)
- `[s32k3xx_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[s32k3xx_dma_alloc.c:s32k3xx_dma_alloc_init]` Initializes/registers kernel devices or filesystems (`gran_initialize()`)
- `[s32k3xx_i2c.c:s32k3xx_i2cdev_initialize]` Initializes/registers kernel devices or filesystems (`i2c_register()`, `s32k3xx_i2cbus_initialize()`)
- `[s32k3xx_selftest.c:s32k3xx_selftest]` Configures or drives hardware GPIO pins
- `[s32k3xx_selftest.c:s32k3xx_selftest]` Initializes/registers kernel devices or filesystems (`s32k3xx_i2cbus_initialize()`)
- `[s32k3xx_spi.c:s32k3xx_spidev_initialize]` Configures or drives hardware GPIO pins
- `[s32k3xx_spi.c:s32k3xx_spidev_initialize]` Initializes/registers kernel devices or filesystems (`fs26_initialize()`, `s32k3xx_lpspibus_initialize()`, `spi_register()`)
- `[s32k3xx_tja1153.c:s32k3xx_tja1153_initialize]` Configures or drives hardware GPIO pins
- `[s32k3xx_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh mr-canhubk3:nsh && make`
