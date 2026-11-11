# `steval-stlcs01v1` Board Support Package (`boards/arm/stm32l4/steval-stlcs01v1`)

## Overview
Board Support Package (BSP) blueprint for `steval-stlcs01v1` (`arm` / `stm32l4`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `lwl`, `usbnsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `steval-stlcs01v1` (`arm/stm32l4`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:STM32_HSI_FREQUENCY]` Hardware/board configuration macros (`STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_BOARD_USEHSI`, `STM32_PLLCFG_PLLM`, `STM32_PLLCFG_PLLN` (+59 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `steval-stlcs01v1` (`arm/stm32l4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
