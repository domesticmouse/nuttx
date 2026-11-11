# `stm32l0538-disco` Board Support Package (`boards/arm/stm32l0/stm32l0538-disco`)

## Overview
Board Support Package (BSP) blueprint for `stm32l0538-disco` (`arm` / `stm32l0`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `stm32l0538-disco` (`arm/stm32l0`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_HSEBYP_ENABLE`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_LSE_FREQUENCY` (+43 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `stm32l0538-disco` (`arm/stm32l0`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
