# `stm32h745i-disco` Board Support Package (`boards/arm/stm32h7/stm32h745i-disco`)

## Overview
Board Support Package (BSP) blueprint for `stm32h745i-disco` (`arm` / `stm32h7`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `lvgl`, `netnsh`, `nsh`, `nsh_cm4`, `nsh_cm4_rptun`, `nsh_cm7` (+2 more).

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `stm32h745i-disco` (`arm/stm32h7`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:STM32_HSI_FREQUENCY]` Hardware/board configuration macros (`STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_BOARD_USEHSE`, `STM32_HSEBYP_ENABLE` (+177 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `stm32h745i-disco` (`arm/stm32h7`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 9 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
