# `stm32l4r9ai-disco/include` Component (`boards/arm/stm32l4/stm32l4r9ai-disco/include`)

## Overview
Board-level public headers (`include`) for `stm32l4r9ai-disco` (`arm/stm32l4`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 3 header file(s).

## Interface
- `[board.h:stm32_board_initialize]` Public declaration `stm32_board_initialize()`
- `[board.h:DMACHAN_SDMMC]` Hardware/board configuration macros (`DMACHAN_SDMMC`, `DMACHAN_SPI1_RX`, `DMACHAN_SPI1_TX`, `DMACHAN_USART1_RX`, `ADC1_MEASURE_CHANNEL`, `GPIO_MEASURE_ADC` (+51 more))
- `[boardctl.h:BIOC_ENTER_MEMMAP]` Hardware/board configuration macros (`BIOC_ENTER_MEMMAP`, `BIOC_EXIT_MEMMAP`)
- `[stm32l4r9ai-disco-clocking.h:STM32_HSI_FREQUENCY]` Hardware/board configuration macros (`STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_SYSCLK_FREQUENCY`, `BOARD_AHB_FREQUENCY` (+47 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh stm32l4r9ai-disco:nsh && make`
