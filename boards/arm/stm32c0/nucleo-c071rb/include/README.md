# `nucleo-c071rb/include` Component (`boards/arm/stm32c0/nucleo-c071rb/include`)

## Overview
Board-level public headers (`include`) for `nucleo-c071rb` (`arm/stm32c0`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_USE_CLK48` (+41 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh nucleo-c071rb:nsh && make`
