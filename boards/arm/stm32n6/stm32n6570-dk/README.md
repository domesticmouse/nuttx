# `stm32n6570-dk` Board Support Package (`boards/arm/stm32n6/stm32n6570-dk`)

## Overview
Board Support Package (BSP) blueprint for `stm32n6570-dk` (`arm` / `stm32n6`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `stm32n6570-dk` (`arm/stm32n6`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:stm32_board_initialize]` Public declaration `stm32_board_initialize()`, `[board.h:STM32_HSI_FREQUENCY]` Hardware/board configuration macros (`STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_BOARD_USEHSE`, `STM32_HSE_FREQUENCY`, `STM32_BOARD_VOS_HIGH` (+85 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `stm32n6570-dk` (`arm/stm32n6`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 6 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
