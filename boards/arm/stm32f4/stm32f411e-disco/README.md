# `stm32f411e-disco` Board Support Package (`boards/arm/stm32f4/stm32f411e-disco`)

## Overview
Board Support Package (BSP) blueprint for `stm32f411e-disco` (`arm` / `stm32f4`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `stm32f411e-disco` (`arm/stm32f4`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_PLLCFG_PLLM`, `STM32_PLLCFG_PLLN` (+80 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `stm32f411e-disco` (`arm/stm32f4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
