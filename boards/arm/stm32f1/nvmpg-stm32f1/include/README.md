# `nvmpg-stm32f1/include` Component (`boards/arm/stm32f1/nvmpg-stm32f1/include`)

## Overview
Board-level public headers (`include`) for `nvmpg-stm32f1` (`arm/stm32f1`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:STM32_HSI_FREQUENCY]` Hardware/board configuration macros (`STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_BOARD_XTAL`, `STM32_HSE_FREQUENCY`, `STM32_CFGR_PLLSRC` (+26 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh nvmpg-stm32f1:dro && make`
