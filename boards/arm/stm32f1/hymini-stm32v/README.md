# `hymini-stm32v` Board Support Package (`boards/arm/stm32f1/hymini-stm32v`)

## Overview
Board Support Package (BSP) blueprint for `hymini-stm32v` (`arm` / `stm32f1`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `nsh2`, `usbmsc`, `usbnsh`, `usbserial`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `hymini-stm32v` (`arm/stm32f1`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_CFGR_PLLSRC`, `STM32_CFGR_PLLXTPRE`, `STM32_CFGR_PLLMUL`, `STM32_PLL_FREQUENCY`, `STM32_SYSCLK_SW` (+89 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `hymini-stm32v` (`arm/stm32f1`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 10 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
