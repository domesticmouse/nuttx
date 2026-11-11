# `viewtool-stm32f107` Board Support Package (`boards/arm/stm32f1/viewtool-stm32f107`)

## Overview
Board Support Package (BSP) blueprint for `viewtool-stm32f107` (`arm` / `stm32f1`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `ft80x`, `highpri`, `netnsh`, `nsh`, `tcpblaster`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `viewtool-stm32f107` (`arm/stm32f1`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 3 header file(s). Key symbols: `[board-stm32f103vct6.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_CFGR_PLLSRC`, `STM32_CFGR_PLLXTPRE`, `STM32_CFGR_PLLMUL`, `STM32_PLL_FREQUENCY`, `STM32_SYSCLK_SW` (+18 more)), `[board-stm32f107vct6.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_PLL_PREDIV2` (+22 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `viewtool-stm32f107` (`arm/stm32f1`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 15 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
