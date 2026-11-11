# `stm32u083c-dk/include` Component (`boards/arm/stm32u0/stm32u083c-dk/include`)

## Overview
Board-level public headers (`include`) for `stm32u083c-dk` (`arm/stm32u0`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_PLLCFG_PLLSRC` (+46 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh stm32u083c-dk:nsh && make`
