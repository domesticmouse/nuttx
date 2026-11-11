# `nucleo-f410rb/include` Component (`boards/arm/stm32f4/nucleo-f410rb/include`)

## Overview
Board-level public headers (`include`) for `nucleo-f410rb` (`arm/stm32f4`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:STM32_HSI_FREQUENCY]` Hardware/board configuration macros (`STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_BOARD_USEHSI`, `STM32_PLLCFG_PLLM`, `STM32_PLLCFG_PLLN`, `STM32_PLLCFG_PLLP` (+58 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh nucleo-f410rb:nsh && make`
