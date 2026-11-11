# `b-u585i-iot02a/include` Component (`boards/arm/stm32u5/b-u585i-iot02a/include`)

## Overview
Board-level public headers (`include`) for `b-u585i-iot02a` (`arm/stm32u5`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:stm32_board_initialize]` Public declaration `stm32_board_initialize()`
- `[board.h:STM32_HSI_FREQUENCY]` Hardware/board configuration macros (`STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_BOARD_USEMSIS`, `STM32_BOARD_MSISRANGE`, `STM32_BOARD_MSIKRANGE` (+35 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh b-u585i-iot02a:nsh && make`
