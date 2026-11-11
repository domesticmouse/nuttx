# `nucleo-l476rg/include` Component (`boards/arm/stm32l4/nucleo-l476rg/include`)

## Overview
Board-level public headers (`include`) for `nucleo-l476rg` (`arm/stm32l4`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s).

## Interface
- `[board.h:DMACHAN_SDMMC]` Hardware/board configuration macros (`DMACHAN_SDMMC`, `DMACHAN_SPI1_RX`, `DMACHAN_SPI1_TX`, `DMACHAN_USART1_RX`, `ADC1_DMA_CHAN`, `ADC2_DMA_CHAN` (+53 more))
- `[nucleo-l476rg.h:HSI_CLOCK_CONFIG]` Hardware/board configuration macros (`HSI_CLOCK_CONFIG`, `HSE_CLOCK_CONFIG`, `MSI_CLOCK_CONFIG`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_LSE_FREQUENCY` (+42 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh nucleo-l476rg:nsh && make`
