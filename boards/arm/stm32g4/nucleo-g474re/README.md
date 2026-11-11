# `nucleo-g474re` Board Support Package (`boards/arm/stm32g4/nucleo-g474re`)

## Overview
Board Support Package (BSP) blueprint for `nucleo-g474re` (`arm` / `stm32g4`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `lpuartnsh`, `nsh`, `usbserial`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `nucleo-g474re` (`arm/stm32g4`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:STM32_HSI_FREQUENCY]` Hardware/board configuration macros (`STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_PLLCFGR_PLLSRC`, `STM32_PLLCFGR_PLLCFG`, `STM32_PLLCFGR_PLLN`, `STM32_PLLCFGR_PLLM` (+46 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `nucleo-g474re` (`arm/stm32g4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 6 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
