# `stm32h573i-dk` Board Support Package (`boards/arm/stm32h5/stm32h573i-dk`)

## Overview
Board Support Package (BSP) blueprint for `stm32h573i-dk` (`arm` / `stm32h5`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `jumbo`, `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `stm32h573i-dk` (`arm/stm32h5`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:STM32_BOARD_USEHSE]` Hardware/board configuration macros (`STM32_BOARD_USEHSE`, `STM32_HSEBYP_ENABLE`, `STM32_HSEEXT_ENABLE`, `STM32_HSE_FREQUENCY`, `STM32_HSI_FREQUENCY`, `STM32_CSI_FREQUENCY` (+67 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `stm32h573i-dk` (`arm/stm32h5`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 6 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
