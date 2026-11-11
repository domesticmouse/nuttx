# `nucleo-l432kc/include` Component (`boards/arm/stm32l4/nucleo-l432kc/include`)

## Overview
Board-level public headers (`include`) for `nucleo-l432kc` (`arm/stm32l4`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s).

## Interface
- `[board.h:stm32_board_initialize]` Public declaration `stm32_board_initialize()`
- `[board.h:DMACHAN_SPI1_RX]` Hardware/board configuration macros (`DMACHAN_SPI1_RX`, `DMACHAN_SPI1_TX`, `DMACHAN_USART1_RX`, `ADC1_DMA_CHAN`, `GPIO_DAC1_OUT`, `GPIO_USART1_RX` (+43 more))
- `[nucleo-l432kc.h:HSI_CLOCK_CONFIG]` Hardware/board configuration macros (`HSI_CLOCK_CONFIG`, `HSE_CLOCK_CONFIG`, `MSI_CLOCK_CONFIG`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_LSE_FREQUENCY` (+38 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh nucleo-l432kc:nsh && make`
