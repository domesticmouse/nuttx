# `nucleo-c092rc` Board Support Package (`boards/arm/stm32c0/nucleo-c092rc`)

## Overview
Board Support Package (BSP) blueprint for `nucleo-c092rc` (`arm` / `stm32c0`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `can`, `cansock`, `jumbo`, `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `nucleo-c092rc` (`arm/stm32c0`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_RCC_HSIDIV` (+45 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `nucleo-c092rc` (`arm/stm32c0`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
