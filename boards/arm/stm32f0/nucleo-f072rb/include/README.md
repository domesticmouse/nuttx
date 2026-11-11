# `nucleo-f072rb/include` Component (`boards/arm/stm32f0/nucleo-f072rb/include`)

## Overview
Board-level public headers (`include`) for `nucleo-f072rb` (`arm/stm32f0`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_HSI_FREQUENCY`, `STM32_HSI14_FREQUENCY`, `STM32_HSI48_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_LSI_FREQUENCY` (+47 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh nucleo-f072rb:nsh && make`
