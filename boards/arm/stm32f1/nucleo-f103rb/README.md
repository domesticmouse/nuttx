# `nucleo-f103rb` Board Support Package (`boards/arm/stm32f1/nucleo-f103rb`)

## Overview
Board Support Package (BSP) blueprint for `nucleo-f103rb` (`arm` / `stm32f1`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `adc`, `ihm07m1_b16`, `nsh`, `pwm`, `qenco`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `nucleo-f103rb` (`arm/stm32f1`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_CFGR_PLLSRC` (+67 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `nucleo-f103rb` (`arm/stm32f1`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 9 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
