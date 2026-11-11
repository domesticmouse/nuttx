# `nucleo-f412zg/include` Component (`boards/arm/stm32f4/nucleo-f412zg/include`)

## Overview
Board-level public headers (`include`) for `nucleo-f412zg` (`arm/stm32f4`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:STM32_BOARD_USEHSE]` Hardware/board configuration macros (`STM32_BOARD_USEHSE`, `STM32_BOARD_XTAL`, `STM32_HSE_FREQUENCY`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_PLLCFG_PLLM` (+60 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh nucleo-f412zg:nsh && make`
