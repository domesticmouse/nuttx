# `b-l072z-lrwan1` Board Support Package (`boards/arm/stm32l0/b-l072z-lrwan1`)

## Overview
Board Support Package (BSP) blueprint for `b-l072z-lrwan1` (`arm` / `stm32l0`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `adc`, `lorawan_beacon`, `lorawan_tx`, `nsh`, `nxlines_oled`, `sx127x`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `b-l072z-lrwan1` (`arm/stm32l0`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_CFGR_PLLSRC` (+66 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `b-l072z-lrwan1` (`arm/stm32l0`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
