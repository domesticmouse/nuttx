# `stm32n6570-dk/include` Component (`boards/arm/stm32n6/stm32n6570-dk/include`)

## Overview
Board-level public headers (`include`) for `stm32n6570-dk` (`arm/stm32n6`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:stm32_board_initialize]` Public declaration `stm32_board_initialize()`
- `[board.h:STM32_HSI_FREQUENCY]` Hardware/board configuration macros (`STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_BOARD_USEHSE`, `STM32_HSE_FREQUENCY`, `STM32_BOARD_VOS_HIGH` (+85 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh stm32n6570-dk:nsh && make`
