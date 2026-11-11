# `stm32f401rc-rs485` Board Support Package (`boards/arm/stm32f4/stm32f401rc-rs485`)

## Overview
Board Support Package (BSP) blueprint for `stm32f401rc-rs485` (`arm` / `stm32f4`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `adc`, `bmp280`, `dac`, `hcsr04`, `lcd1602`, `lm75` (+13 more).

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `stm32f401rc-rs485` (`arm/stm32f4`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:STM32_HSI_FREQUENCY]` Hardware/board configuration macros (`STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_BOARD_USEHSI`, `STM32_PLLCFG_PLLM`, `STM32_PLLCFG_PLLN`, `STM32_PLLCFG_PLLP` (+102 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `stm32f401rc-rs485` (`arm/stm32f4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 17 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
