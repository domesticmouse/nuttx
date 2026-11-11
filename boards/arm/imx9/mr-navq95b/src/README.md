# `mr-navq95b/src` Component (`boards/arm/imx9/mr-navq95b/src`)

## Overview
Board-level C implementation (`src`) for `mr-navq95b` (`arm/imx9`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[mr-navq95b.h:imx95_bringup]` Public declaration `imx95_bringup()`
- `[mr-navq95b.h:imx95_pwm_setup]` Public declaration `imx95_pwm_setup()`
- `[mr-navq95b.h:imx95_i2c_initialize]` Public declaration `imx95_i2c_initialize()`
- `[mr-navq95b.h:imx95_spi_initialize]` Public declaration `imx95_spi_initialize()`
- `[imx95_boardinit.c:imx95_memory_initialize]` Public function `imx95_memory_initialize()`
- `[imx95_boardinit.c:imx9_boardinitialize]` Public function `imx9_boardinitialize()`
- `[imx95_boardinit.c:board_late_initialize]` Public function `board_late_initialize()`
- `[imx95_bringup.c:rpmsg_serialinit]` Public function `rpmsg_serialinit()`
- `[imx95_bringup.c:imx95_bringup]` Public function `imx95_bringup()`
- `[imx95_i2c.c:imx95_i2c_initialize]` Public function `imx95_i2c_initialize()`
- `[imx95_spi.c:imx9_lpspi_select]` Public function `imx9_lpspi_select()`
- `[imx95_spi.c:imx9_lpspi_status]` Public function `imx9_lpspi_status()`
- `[imx95_spi.c:imx95_lpspi_cmddata]` Public function `imx95_lpspi_cmddata()`
- `[imx95_spi.c:imx95_spi_initialize]` Public function `imx95_spi_initialize()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_IMX9_LPI2C`, `CONFIG_IMX9_LPSPI`, `CONFIG_PWM`
- `[imx95_i2c.c:imx95_i2c_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[imx95_spi.c:imx9_lpspi_select]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[imx95_bringup.c:rpmsg_serialinit]` Initializes/registers kernel devices or filesystems (`imx95_i2c_initialize()`, `imx95_spi_initialize()`, `nx_mount()`)
- `[imx95_i2c.c:imx95_i2c_initialize]` Initializes/registers kernel devices or filesystems (`i2c_register()`, `imx9_i2cbus_initialize()`)
- `[imx95_spi.c:imx9_lpspi_select]` Initializes/registers kernel devices or filesystems (`imx9_lpspibus_initialize()`, `spi_register()`)

## Verification
- Run: `./tools/configure.sh mr-navq95b:nsh && make`
