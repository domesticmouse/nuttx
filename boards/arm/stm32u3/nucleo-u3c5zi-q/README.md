# `nucleo-u3c5zi-q` Board Support Package (`boards/arm/stm32u3/nucleo-u3c5zi-q`)

## Overview
Board Support Package (BSP) blueprint for `nucleo-u3c5zi-q` (`arm` / `stm32u3`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `jumbo`, `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `nucleo-u3c5zi-q` (`arm/stm32u3`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:stm32_board_initialize]` Public declaration `stm32_board_initialize()`, `[board.h:STM32_BOARD_USEMSIS]` Hardware/board configuration macros (`STM32_BOARD_USEMSIS`, `STM32_RCC_ICSCR1_MSISSEL`, `STM32_RCC_ICSCR1_MSISDIV`, `STM32_RCC_CFGR4_BOOSTSEL`, `STM32_RCC_CFGR4_BOOSTDIV`, `STM32_PWR_CR3_REGSEL` (+46 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `nucleo-u3c5zi-q` (`arm/stm32u3`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 3 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
