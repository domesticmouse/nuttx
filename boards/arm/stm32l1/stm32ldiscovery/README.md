# `stm32ldiscovery` Board Support Package (`boards/arm/stm32l1/stm32ldiscovery`)

## Overview
Board Support Package (BSP) blueprint for `stm32ldiscovery` (`arm` / `stm32l1`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `chrono`, `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `stm32ldiscovery` (`arm/stm32l1`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:stm32_slcd_initialize]` Public declaration `stm32_slcd_initialize()`, `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_HSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_MSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_LSE_FREQUENCY` (+45 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `stm32ldiscovery` (`arm/stm32l1`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 9 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
