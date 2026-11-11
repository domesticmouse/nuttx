# `b-g431b-esc1` Board Support Package (`boards/arm/stm32g4/b-g431b-esc1`)

## Overview
Board Support Package (BSP) blueprint for `b-g431b-esc1` (`arm` / `stm32g4`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `can`, `cansock`, `foc_b16`, `foc_f32`, `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `b-g431b-esc1` (`arm/stm32g4`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_PLLCFGR_PLLSRC`, `STM32_PLLCFGR_PLLCFG` (+81 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `b-g431b-esc1` (`arm/stm32g4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 9 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
