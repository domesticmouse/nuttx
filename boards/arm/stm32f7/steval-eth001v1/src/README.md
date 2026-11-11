# `steval-eth001v1/src` Component (`boards/arm/stm32f7/steval-eth001v1/src`)

## Overview
Board-level C implementation (`src`) for `steval-eth001v1` (`arm/stm32f7`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[steval-eth001v1.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[steval-eth001v1.h:stm32_foc_setup]` Public declaration `stm32_foc_setup()`
- `[steval-eth001v1.h:stm32_adc_setup]` Public declaration `stm32_adc_setup()`
- `[steval-eth001v1.h:STM32_PROCFS_MOUNTPOINT]` Hardware/board configuration macros (`STM32_PROCFS_MOUNTPOINT`)
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- `[stm32_foc.c:stm32_foc_setup]` Public function `stm32_foc_setup()`
- `[stm32_foc.c:stm32_adc_setup]` Public function `stm32_adc_setup()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_STM32_FOC`
- `[stm32_foc.c:DEBUGASSERT]` Requires `dev`
- `[stm32_foc.c:#error]` Compile-time guard: `Only 3-shunts configuration is supported`
- `[stm32_foc.c:#error]` Compile-time guard: `#endif`

## Side Effects
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`nx_mount()`)
- `[stm32_foc.c:stm32_foc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`, `foc_register()`, `stm32_foc_initialize()`)

## Verification
- Run: `./tools/configure.sh steval-eth001v1:nsh && make`
