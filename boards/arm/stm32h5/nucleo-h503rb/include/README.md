# `nucleo-h503rb/include` Component (`boards/arm/stm32h5/nucleo-h503rb/include`)

## Overview
Board-level public headers (`include`) for `nucleo-h503rb` (`arm/stm32h5`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:stm32_board_initialize]` Public declaration `stm32_board_initialize()`
- `[board.h:STM32_SYSCLK_FREQUENCY]` Hardware/board configuration macros (`STM32_SYSCLK_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_BOARD_USEHSI`, `STM32_BOARD_HSIDIV`, `STM32_HSI_FREQUENCY` (+53 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh nucleo-h503rb:nsh && make`
