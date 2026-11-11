# `stm32f429i-disco` Board Support Package (`boards/arm/stm32f4/stm32f429i-disco`)

## Overview
Board Support Package (BSP) blueprint for `stm32f429i-disco` (`arm` / `stm32f4`). Coordinates board initialization, headers, and tooling across `include, src, tools`. Includes build configurations: `adc`, `bootlogo`, `extflash`, `fb`, `gdbstub`, `highpri` (+10 more).

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `stm32f429i-disco` (`arm/stm32f4`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_PLLCFG_PLLM` (+172 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `stm32f429i-disco` (`arm/stm32f4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 17 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
- [`tools`](./tools/README.md) - Board support component `tools` for `stm32f429i-disco` (`arm/stm32f4`), containing 1 source/script file(s) (`fbcalc.sh`). Key symbols: `[fbcalc.sh]` Shell script entry point `fbcalc.sh`.
