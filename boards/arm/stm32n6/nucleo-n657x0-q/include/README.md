# `nucleo-n657x0-q/include` Component (`boards/arm/stm32n6/nucleo-n657x0-q/include`)

## Overview
Board-level public headers (`include`) for `nucleo-n657x0-q` (`arm/stm32n6`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:stm32_board_initialize]` Public declaration `stm32_board_initialize()`
- `[board.h:STM32_HSI_FREQUENCY]` Hardware/board configuration macros (`STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_PLL1_SRC`, `STM32_PLL1_M`, `STM32_PLL1_N` (+67 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh nucleo-n657x0-q:nsh && make`
