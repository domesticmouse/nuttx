# `steval-stlcs01v1/include` Component (`boards/arm/stm32l4/steval-stlcs01v1/include`)

## Overview
Board-level public headers (`include`) for `steval-stlcs01v1` (`arm/stm32l4`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:STM32_HSI_FREQUENCY]` Hardware/board configuration macros (`STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_BOARD_USEHSI`, `STM32_PLLCFG_PLLM`, `STM32_PLLCFG_PLLN` (+59 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh steval-stlcs01v1:lwl && make`
