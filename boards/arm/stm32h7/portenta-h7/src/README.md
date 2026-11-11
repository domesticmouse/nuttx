# `portenta-h7/src` Component (`boards/arm/stm32h7/portenta-h7/src`)

## Overview
Board-level C implementation (`src`) for `portenta-h7` (`arm/stm32h7`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[portenta-h7.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[portenta-h7.h:STM32_PROCFS_MOUNTPOINT]` Hardware/board configuration macros (`STM32_PROCFS_MOUNTPOINT`, `GPIO_LD1`, `GPIO_LD2`, `GPIO_LD3`, `GPIO_LED_RED`, `GPIO_LED_GREEN` (+3 more))
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_LEDS`
- `[stm32_autoleds.c:#error]` Compile-time guard: `autoleds not supported for M4 core now`

## Side Effects
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`i2c_register()`, `nx_mount()`, `stm32_i2c_register()`, `stm32_i2cbus_initialize()`)

## Verification
- Run: `./tools/configure.sh portenta-h7:jumbo_cm7 && make`
