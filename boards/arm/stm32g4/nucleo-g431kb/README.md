# `nucleo-g431kb` Board Support Package (`boards/arm/stm32g4/nucleo-g431kb`)

## Overview
Board Support Package (BSP) blueprint for `nucleo-g431kb` (`arm` / `stm32g4`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `comp`, `nsh`, `pwm`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `nucleo-g431kb` (`arm/stm32g4`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_PLLCFGR_PLLSRC`, `STM32_PLLCFGR_PLLCFG` (+51 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `nucleo-g431kb` (`arm/stm32g4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
