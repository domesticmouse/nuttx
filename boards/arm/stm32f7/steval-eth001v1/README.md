# `steval-eth001v1` Board Support Package (`boards/arm/stm32f7/steval-eth001v1`)

## Overview
Board Support Package (BSP) blueprint for `steval-eth001v1` (`arm` / `stm32f7`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `foc_b16`, `foc_f32`, `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `steval-eth001v1` (`arm/stm32f7`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_PLLCFG_PLLM` (+83 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `steval-eth001v1` (`arm/stm32f7`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
