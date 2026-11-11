# `nucleo-h743zi/include` Component (`boards/arm/stm32h7/nucleo-h743zi/include`)

## Overview
Board-level public headers (`include`) for `nucleo-h743zi` (`arm/stm32h7`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_BOARD_USEHSE` (+183 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh nucleo-h743zi:nsh && make`
