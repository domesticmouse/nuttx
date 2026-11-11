# `olimex-stm32-h407` Board Support Package (`boards/arm/stm32f4/olimex-stm32-h407`)

## Overview
Board Support Package (BSP) blueprint for `olimex-stm32-h407` (`arm` / `stm32f4`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `nsh_uext`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `olimex-stm32-h407` (`arm/stm32f4`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_PLLCFG_PLLM` (+66 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `olimex-stm32-h407` (`arm/stm32f4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 10 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
