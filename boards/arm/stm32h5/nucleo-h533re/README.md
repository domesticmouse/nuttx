# `nucleo-h533re` Board Support Package (`boards/arm/stm32h5/nucleo-h533re`)

## Overview
Board Support Package (BSP) blueprint for `nucleo-h533re` (`arm` / `stm32h5`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `nucleo-h533re` (`arm/stm32h5`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:stm32_board_initialize]` Public declaration `stm32_board_initialize()`, `[board.h:STM32_SYSCLK_FREQUENCY]` Hardware/board configuration macros (`STM32_SYSCLK_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_BOARD_USEHSI`, `STM32_BOARD_HSIDIV`, `STM32_HSI_FREQUENCY` (+58 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `nucleo-h533re` (`arm/stm32h5`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 6 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
