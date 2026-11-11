# `flipperzero/include` Component (`boards/arm/stm32wb/flipperzero/include`)

## Overview
Board-level public headers (`include`) for `flipperzero` (`arm/stm32wb`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s).

## Interface
- `[board.h:stm32_board_initialize]` Public declaration `stm32_board_initialize()`
- `[board.h:GPIO_USART1_TX]` Hardware/board configuration macros (`GPIO_USART1_TX`, `GPIO_USART1_RX`, `GPIO_SPI2_SCK`, `GPIO_SPI2_MISO`, `GPIO_SPI2_MOSI`, `LED_STARTED` (+18 more))
- `[flipperzero-clocking.h:STM32_HSI_FREQUENCY]` Hardware/board configuration macros (`STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_HSE_FREQUENCY`, `HSI_CLOCK_CONFIG`, `HSE_CLOCK_CONFIG` (+33 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh flipperzero:nsh && make`
