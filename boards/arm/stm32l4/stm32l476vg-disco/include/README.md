# `stm32l476vg-disco/include` Component (`boards/arm/stm32l4/stm32l476vg-disco/include`)

## Overview
Board-level public headers (`include`) for `stm32l476vg-disco` (`arm/stm32l4`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 3 header file(s).

## Interface
- `[board.h:stm32_board_initialize]` Public declaration `stm32_board_initialize()`
- `[board.h:DMACHAN_SDMMC]` Hardware/board configuration macros (`DMACHAN_SDMMC`, `DMACHAN_SPI1_RX`, `DMACHAN_SPI1_TX`, `DMACHAN_USART1_RX`, `GPIO_USART1_RX`, `GPIO_USART1_TX` (+53 more))
- `[boardctl.h:BIOC_ENTER_MEMMAP]` Hardware/board configuration macros (`BIOC_ENTER_MEMMAP`, `BIOC_EXIT_MEMMAP`)
- `[stm32l476vg-disco-clocking.h:STM32_HSI_FREQUENCY]` Hardware/board configuration macros (`STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_LSE_FREQUENCY`, `BOARD_AHB_FREQUENCY`, `HSI_CLOCK_CONFIG`, `HSE_CLOCK_CONFIG` (+43 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh stm32l476vg-disco:nsh && make`
