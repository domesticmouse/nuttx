# `stm32h750b-dk` Board Support Package (`boards/arm/stm32h7/stm32h750b-dk`)

## Overview
Board Support Package (BSP) blueprint for `stm32h750b-dk` (`arm` / `stm32h7`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `lvgl`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `stm32h750b-dk` (`arm/stm32h7`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:STM32_HSI_FREQUENCY]` Hardware/board configuration macros (`STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_BOARD_USEHSE`, `STM32_HSEBYP_ENABLE` (+177 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `stm32h750b-dk` (`arm/stm32h7`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 9 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
