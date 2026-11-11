# `stm32f411e-disco/include` Component (`boards/arm/stm32f4/stm32f411e-disco/include`)

## Overview
Board-level public headers (`include`) for `stm32f411e-disco` (`arm/stm32f4`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_PLLCFG_PLLM`, `STM32_PLLCFG_PLLN` (+80 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh stm32f411e-disco:nsh && make`
