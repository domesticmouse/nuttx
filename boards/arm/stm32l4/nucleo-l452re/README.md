# `nucleo-l452re` Board Support Package (`boards/arm/stm32l4/nucleo-l452re`)

## Overview
Board Support Package (BSP) blueprint for `nucleo-l452re` (`arm` / `stm32l4`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `nucleo-l452re` (`arm/stm32l4`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s). Key symbols: `[board.h:stm32_board_initialize]` Public declaration `stm32_board_initialize()`, `[board.h:DMACHAN_SDMMC]` Hardware/board configuration macros (`DMACHAN_SDMMC`, `DMACHAN_SPI1_RX`, `DMACHAN_SPI1_TX`, `DMACHAN_USART1_RX`, `ADC1_DMA_CHAN`, `GPIO_USART1_RX` (+50 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `nucleo-l452re` (`arm/stm32l4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 9 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
