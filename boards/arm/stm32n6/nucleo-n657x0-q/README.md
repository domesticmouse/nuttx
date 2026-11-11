# `nucleo-n657x0-q` Board Support Package (`boards/arm/stm32n6/nucleo-n657x0-q`)

## Overview
Board Support Package (BSP) blueprint for `nucleo-n657x0-q` (`arm` / `stm32n6`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `leds`, `nsh`, `ostest`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `nucleo-n657x0-q` (`arm/stm32n6`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:stm32_board_initialize]` Public declaration `stm32_board_initialize()`, `[board.h:STM32_HSI_FREQUENCY]` Hardware/board configuration macros (`STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_PLL1_SRC`, `STM32_PLL1_M`, `STM32_PLL1_N` (+67 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `nucleo-n657x0-q` (`arm/stm32n6`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
