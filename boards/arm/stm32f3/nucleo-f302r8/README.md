# `nucleo-f302r8` Board Support Package (`boards/arm/stm32f3/nucleo-f302r8`)

## Overview
Board Support Package (BSP) blueprint for `nucleo-f302r8` (`arm` / `stm32f3`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `can`, `cansock`, `highpri`, `ihm07m1_b16`, `ihm07m1_f32`, `nsh` (+1 more).

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `nucleo-f302r8` (`arm/stm32f3`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_CFGR_PLLSRC` (+69 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `nucleo-f302r8` (`arm/stm32f3`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 10 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
