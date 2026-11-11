# `nucleo-l552ze/include` Component (`boards/arm/stm32l5/nucleo-l552ze/include`)

## Overview
Board-level public headers (`include`) for `nucleo-l552ze` (`arm/stm32l5`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:stm32_board_initialize]` Public declaration `stm32_board_initialize()`
- `[board.h:STM32_HSI_FREQUENCY]` Hardware/board configuration macros (`STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_BOARD_USEMSI`, `STM32_BOARD_MSIRANGE`, `STM32_PLLCFG_PLLM` (+63 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh nucleo-l552ze:nsh && make`
