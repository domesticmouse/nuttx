# `stm32l476-mdk/include` Component (`boards/arm/stm32l4/stm32l476-mdk/include`)

## Overview
Board-level public headers (`include`) for `stm32l476-mdk` (`arm/stm32l4`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s).

## Interface
- `[board.h:stm32_board_initialize]` Public declaration `stm32_board_initialize()`
- `[board.h:GPIO_USART1_CTS]` Hardware/board configuration macros (`GPIO_USART1_CTS`, `GPIO_USART1_RTS`, `GPIO_USART1_RX`, `GPIO_USART1_TX`, `GPIO_USART2_CTS`, `GPIO_USART2_RTS` (+36 more))
- `[stm32l476-mdk-clocking.h:STM32_HSI_FREQUENCY]` Hardware/board configuration macros (`STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_LSE_FREQUENCY`, `BOARD_AHB_FREQUENCY`, `HSI_CLOCK_CONFIG`, `MSI_CLOCK_CONFIG` (+41 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh stm32l476-mdk:nsh && make`
