# `nucleo-c562re/include` Component (`boards/arm/stm32c5/nucleo-c562re/include`)

## Overview
Board-level public headers (`include`) for `nucleo-c562re` (`arm/stm32c5`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:stm32_board_initialize]` Public declaration `stm32_board_initialize()`
- `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_HSE_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_BOARD_USEHSE`, `STM32_BOARD_USEPSI` (+43 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh nucleo-c562re:nsh && make`
