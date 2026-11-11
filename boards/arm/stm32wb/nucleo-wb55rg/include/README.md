# `nucleo-wb55rg/include` Component (`boards/arm/stm32wb/nucleo-wb55rg/include`)

## Overview
Board-level public headers (`include`) for `nucleo-wb55rg` (`arm/stm32wb`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s).

## Interface
- `[board.h:stm32_board_initialize]` Public declaration `stm32_board_initialize()`
- `[board.h:DMAMAP_SPI1_RX]` Hardware/board configuration macros (`DMAMAP_SPI1_RX`, `DMAMAP_SPI1_TX`, `DMAMAP_USART1_RX`, `DMAMAP_ADC1`, `GPIO_USART1_RX`, `GPIO_USART1_TX` (+43 more))
- `[nucleo-wb55rg.h:STM32_HSI_FREQUENCY]` Hardware/board configuration macros (`STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_HSE_FREQUENCY`, `HSI_CLOCK_CONFIG`, `HSE_CLOCK_CONFIG` (+35 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh nucleo-wb55rg:nsh && make`
