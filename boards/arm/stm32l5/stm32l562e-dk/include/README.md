# `stm32l562e-dk/include` Component (`boards/arm/stm32l5/stm32l562e-dk/include`)

## Overview
Board-level public headers (`include`) for `stm32l562e-dk` (`arm/stm32l5`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:stm32_board_initialize]` Public declaration `stm32_board_initialize()`
- `[board.h:STM32_HSI_FREQUENCY]` Hardware/board configuration macros (`STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_MSI_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_SYSCLK_FREQUENCY`, `STM32_HCLK_FREQUENCY` (+36 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh stm32l562e-dk:nsh && make`
