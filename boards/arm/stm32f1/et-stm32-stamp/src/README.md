# `et-stm32-stamp/src` Component (`boards/arm/stm32f1/et-stm32-stamp/src`)

## Overview
Board-level C implementation (`src`) for `et-stm32-stamp` (`arm/stm32f1`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 2 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[et-stm32-stamp.h]` Board header declarations `et-stm32-stamp.h`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh et-stm32-stamp:nsh && make`
