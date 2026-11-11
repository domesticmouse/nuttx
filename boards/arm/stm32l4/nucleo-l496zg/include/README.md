# `nucleo-l496zg/include` Component (`boards/arm/stm32l4/nucleo-l496zg/include`)

## Overview
Board-level public headers (`include`) for `nucleo-l496zg` (`arm/stm32l4`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:stm32_board_initialize]` Public declaration `stm32_board_initialize()`
- `[board.h:STM32_HSI_FREQUENCY]` Hardware/board configuration macros (`STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_LSE_FREQUENCY`, `MSI_CLOCK_CONFIG`, `STM32_BOARD_USEHSI` (+97 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh nucleo-l496zg:nsh && make`
