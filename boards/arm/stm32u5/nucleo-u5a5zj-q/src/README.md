# `nucleo-u5a5zj-q/src` Component (`boards/arm/stm32u5/nucleo-u5a5zj-q/src`)

## Overview
Board-level C implementation (`src`) for `nucleo-u5a5zj-q` (`arm/stm32u5`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[nucleo-u5a5zj-q.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[nucleo-u5a5zj-q.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[nucleo-u5a5zj-q.h:HAVE_RTC_DRIVER]` Hardware/board configuration macros (`HAVE_RTC_DRIVER`)
- `[stm32_boot.c:stm32_board_initialize]` Public function `stm32_board_initialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:up_rtc_initialize]` Public function `up_rtc_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- `[stm32_clockconfig.c:stm32_board_clockconfig]` Public function `stm32_board_clockconfig()`
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

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BOARD_STM32_CUSTOM_CLOCKCONFIG`
- `[stm32_spi.c:stm32_spidev_initialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[stm32_boot.c:stm32_board_initialize]` Initializes/registers kernel devices or filesystems (`stm32_spidev_initialize()`)
- `[stm32_bringup.c:up_rtc_initialize]` Initializes/registers kernel devices or filesystems (`dsxxxx_rtc_initialize()`, `stm32_common_initialize()`, `stm32_i2cbus_initialize()`)
- `[stm32_spi.c:stm32_spidev_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh nucleo-u5a5zj-q:nsh && make`
