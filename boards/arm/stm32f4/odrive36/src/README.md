# `odrive36/src` Component (`boards/arm/stm32f4/odrive36/src`)

## Overview
Board-level C implementation (`src`) for `odrive36` (`arm/stm32f4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 6 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[odrive.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[odrive.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[odrive.h:stm32_adc_setup]` Public declaration `stm32_adc_setup()`
- `[odrive.h:stm32_dac_setup]` Public declaration `stm32_dac_setup()`
- `[odrive.h:stm32_foc_setup]` Public declaration `stm32_foc_setup()`
- `[odrive.h:stm32_usbinitialize]` Public declaration `stm32_usbinitialize()`
- `[odrive.h:STM32_PROCFS_MOUNTPOINT]` Hardware/board configuration macros (`STM32_PROCFS_MOUNTPOINT`, `GPIO_DRV8301_ENGATE`, `GPIO_DRV8301_NFAULT`, `GPIO_GATEDRV0_CS`, `GPIO_GATEDRV1_CS`, `GPIO_QE3_INDEX` (+1 more))
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- `[stm32_foc.c:stm32_foc_setup]` Public function `stm32_foc_setup()`
- `[stm32_foc.c:stm32_adc_setup]` Public function `stm32_adc_setup()`
- `[stm32_spi.c:stm32_spidev_initialize]` Public function `stm32_spidev_initialize()`
- `[stm32_spi.c:stm32_spi1select]` Public function `stm32_spi1select()`
- `[stm32_spi.c:stm32_spi1status]` Public function `stm32_spi1status()`
- `[stm32_spi.c:stm32_spi2select]` Public function `stm32_spi2select()`
- `[stm32_spi.c:stm32_spi2status]` Public function `stm32_spi2status()`
- `[stm32_spi.c:stm32_spi3select]` Public function `stm32_spi3select()`
- `[stm32_spi.c:stm32_spi3status]` Public function `stm32_spi3status()`
- `[stm32_spi.c:stm32_spi1cmddata]` Public function `stm32_spi1cmddata()`
- `[stm32_spi.c:stm32_spi2cmddata]` Public function `stm32_spi2cmddata()`
- `[stm32_spi.c:stm32_spi3cmddata]` Public function `stm32_spi3cmddata()`
- `[stm32_usb.c:stm32_usbinitialize]` Public function `stm32_usbinitialize()`
- *(+1 additional symbols across 6 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_STM32_FOC`, `CONFIG_STM32_OTGFS`, `CONFIG_STM32_SPI`
- `[stm32_foc.c:DEBUGASSERT]` Requires `dev`
- `[stm32_foc.c:DEBUGASSERT]` Requires `dev->pwr`
- `[stm32_foc.c:#error]` Compile-time guard: `Tested only for ODrive 56V version`
- `[stm32_foc.c:#error]` Compile-time guard: `Invalid configuration`
- `[stm32_spi.c:stm32_spidev_initialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `stm32_spidev_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`board_qencoder_initialize()`, `cdcacm_initialize()`, `nx_mount()`)
- `[stm32_foc.c:stm32_foc_setup]` Configures or drives hardware GPIO pins
- `[stm32_foc.c:stm32_foc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`, `drv8301_register()`, `stm32_foc_initialize()`, `stm32_spibus_initialize()`)
- `[stm32_spi.c:stm32_spidev_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh odrive36:nsh && make`
