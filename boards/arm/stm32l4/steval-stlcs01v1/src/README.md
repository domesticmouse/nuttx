# `steval-stlcs01v1/src` Component (`boards/arm/stm32l4/steval-stlcs01v1/src`)

## Overview
Board-level C implementation (`src`) for `steval-stlcs01v1` (`arm/stm32l4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[steval-stlcs01v1.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[steval-stlcs01v1.h:stm32_usbinitialize]` Public declaration `stm32_usbinitialize()`
- `[steval-stlcs01v1.h:GPIO_LD1]` Hardware/board configuration macros (`GPIO_LD1`, `GPIO_LSM6DS3H_CS`, `GPIO_LPS22HB_CS`, `GPIO_LSM303AGR_M_CS`, `GPIO_LSM303AGR_A_CS`, `GPIO_BLUE_CS` (+1 more))
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_boot.c:stm32_board_initialize]` Public function `stm32_board_initialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- `[stm32_usb.c:stm32_usbinitialize]` Public function `stm32_usbinitialize()`
- `[stm32_usb.c:stm32_usbsuspend]` Public function `stm32_usbsuspend()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_LEDS`, `CONFIG_STM32_OTGFS`

## Side Effects
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_board_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)

## Verification
- Run: `./tools/configure.sh steval-stlcs01v1:lwl && make`
