# `linum-stm32h753bi` Board Support Package (`boards/arm/stm32h7/linum-stm32h753bi`)

## Overview
Board Support Package (BSP) blueprint for `linum-stm32h753bi` (`arm` / `stm32h7`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `buzzer`, `curl`, `eeprom`, `leds`, `littlefs`, `lvgl` (+20 more).

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `linum-stm32h753bi` (`arm/stm32h7`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:STM32_HSI_FREQUENCY]` Hardware/board configuration macros (`STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_BOARD_USEHSE`, `STM32_PLLCFG_PLLSRC` (+200 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `linum-stm32h753bi` (`arm/stm32h7`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 16 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
