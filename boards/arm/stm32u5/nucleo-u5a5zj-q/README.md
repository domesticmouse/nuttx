# `nucleo-u5a5zj-q` Board Support Package (`boards/arm/stm32u5/nucleo-u5a5zj-q`)

## Overview
Board Support Package (BSP) blueprint for `nucleo-u5a5zj-q` (`arm` / `stm32u5`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `nucleo-u5a5zj-q` (`arm/stm32u5`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:stm32_board_initialize]` Public declaration `stm32_board_initialize()`, `[board.h:STM32_HSI_FREQUENCY]` Hardware/board configuration macros (`STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_BOARD_USEMSIS`, `STM32_BOARD_MSISRANGE`, `STM32_BOARD_MSIKRANGE` (+41 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `nucleo-u5a5zj-q` (`arm/stm32u5`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
