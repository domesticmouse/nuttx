# `b-g474e-dpow1` Board Support Package (`boards/arm/stm32g4/b-g474e-dpow1`)

## Overview
Board Support Package (BSP) blueprint for `b-g474e-dpow1` (`arm` / `stm32g4`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `buckboost`, `nsh`, `ostest`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `b-g474e-dpow1` (`arm/stm32g4`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:STM32_HSI_FREQUENCY]` Hardware/board configuration macros (`STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_PLLCFGR_PLLSRC`, `STM32_PLLCFGR_PLLCFG`, `STM32_PLLCFGR_PLLN`, `STM32_PLLCFGR_PLLM` (+82 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `b-g474e-dpow1` (`arm/stm32g4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
