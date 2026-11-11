# `stm32l562e-dk` Board Support Package (`boards/arm/stm32l5/stm32l562e-dk`)

## Overview
Board Support Package (BSP) blueprint for `stm32l562e-dk` (`arm` / `stm32l5`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `stm32l562e-dk` (`arm/stm32l5`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:stm32_board_initialize]` Public declaration `stm32_board_initialize()`, `[board.h:STM32_HSI_FREQUENCY]` Hardware/board configuration macros (`STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_MSI_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_SYSCLK_FREQUENCY`, `STM32_HCLK_FREQUENCY` (+36 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `stm32l562e-dk` (`arm/stm32l5`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
