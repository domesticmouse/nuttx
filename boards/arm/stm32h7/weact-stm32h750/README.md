# `weact-stm32h750` Board Support Package (`boards/arm/stm32h7/weact-stm32h750`)

## Overview
Board Support Package (BSP) blueprint for `weact-stm32h750` (`arm` / `stm32h7`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `sdcard`, `st7735`, `usbnsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `weact-stm32h750` (`arm/stm32h7`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_BOARD_USEHSE` (+100 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `weact-stm32h750` (`arm/stm32h7`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 10 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
