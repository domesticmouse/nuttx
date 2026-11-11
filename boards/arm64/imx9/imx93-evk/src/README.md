# `imx93-evk/src` Component (`boards/arm64/imx9/imx93-evk/src`)

## Overview
Board-level C implementation (`src`) for `imx93-evk` (`arm64/imx9`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 9 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[imx93-evk.h:imx9_bringup]` Public declaration `imx9_bringup()`
- `[imx93-evk.h:imx9_pwm_setup]` Public declaration `imx9_pwm_setup()`
- `[imx93-evk.h:imx9_dshot_setup]` Public declaration `imx9_dshot_setup()`
- `[imx93-evk.h:imx9_i2c_initialize]` Public declaration `imx9_i2c_initialize()`
- `[imx93-evk.h:imx9_spi_initialize]` Public declaration `imx9_spi_initialize()`
- `[imx93-evk.h:imx9_usdhc_init]` Public declaration `imx9_usdhc_init()`
- `[imx93-evk.h:SDIO_SLOTNO]` Hardware/board configuration macros (`SDIO_SLOTNO`, `SDIO_MINOR`)
- `[imx9_boardinit.c:imx9_memory_initialize]` Public function `imx9_memory_initialize()`
- `[imx9_boardinit.c:imx9_board_initialize]` Public function `imx9_board_initialize()`
- `[imx9_boardinit.c:board_late_initialize]` Public function `board_late_initialize()`
- `[imx9_bringup.c:imx9_bringup]` Public function `imx9_bringup()`
- `[imx9_ddr_config.c:imx9_ddr_config]` Public function `imx9_ddr_config()`
- `[imx9_dshot.c:imx9_dshot_setup]` Public function `imx9_dshot_setup()`
- `[imx9_i2c.c:imx9_i2c_initialize]` Public function `imx9_i2c_initialize()`
- `[imx9_pwm.c:imx9_pwm_setup]` Public function `imx9_pwm_setup()`
- `[imx9_spi.c:imx9_lpspi_select]` Public function `imx9_lpspi_select()`
- `[imx9_spi.c:imx9_lpspi_status]` Public function `imx9_lpspi_status()`
- `[imx9_spi.c:imx9_lpspi_cmddata]` Public function `imx9_lpspi_cmddata()`
- `[imx9_spi.c:imx9_spi_initialize]` Public function `imx9_spi_initialize()`
- `[imx9_usdhc.c:imx9_usdhc_init]` Public function `imx9_usdhc_init()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_DSHOT`, `CONFIG_IMX9_BOOTLOADER`, `CONFIG_IMX9_DDR_TRAINING`, `CONFIG_IMX9_LPI2C`, `CONFIG_IMX9_LPSPI`, `CONFIG_IMX9_USDHC` (+1 more)
- `[imx9_dshot.c:imx9_dshot_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[imx9_i2c.c:imx9_i2c_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[imx9_pwm.c:imx9_pwm_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[imx9_spi.c:imx9_lpspi_select]` Validates preconditions and returns `-ENODEV` on failure
- `[imx9_usdhc.c:imx9_usdhc_init]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[imx9_bringup.c:imx9_bringup]` Initializes/registers kernel devices or filesystems (`imx9_i2c_initialize()`, `imx9_spi_initialize()`, `nx_mount()`, `romdisk_register()`)
- `[imx9_dshot.c:imx9_dshot_setup]` Initializes/registers kernel devices or filesystems (`dshot_register()`)
- `[imx9_i2c.c:imx9_i2c_initialize]` Initializes/registers kernel devices or filesystems (`i2c_register()`, `imx9_i2cbus_initialize()`)
- `[imx9_pwm.c:imx9_pwm_setup]` Initializes/registers kernel devices or filesystems (`pwm_register()`)
- `[imx9_spi.c:imx9_lpspi_select]` Initializes/registers kernel devices or filesystems (`imx9_lpspibus_initialize()`, `spi_register()`)
- `[imx9_usdhc.c:imx9_usdhc_init]` Initializes/registers kernel devices or filesystems (`imx9_usdhc_initialize()`)

## Verification
- Run: `./tools/configure.sh imx93-evk:nsh && make`
