# `nvmpg-stm32f1` Board Support Package (`boards/arm/stm32f1/nvmpg-stm32f1`)

## Overview
Board Support Package (BSP) blueprint for `nvmpg-stm32f1` (`arm` / `stm32f1`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `dro`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `nvmpg-stm32f1` (`arm/stm32f1`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:STM32_HSI_FREQUENCY]` Hardware/board configuration macros (`STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_BOARD_XTAL`, `STM32_HSE_FREQUENCY`, `STM32_CFGR_PLLSRC` (+26 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `nvmpg-stm32f1` (`arm/stm32f1`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
