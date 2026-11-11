# `nucleo-wb55rg` Board Support Package (`boards/arm/stm32wb/nucleo-wb55rg`)

## Overview
Board Support Package (BSP) blueprint for `nucleo-wb55rg` (`arm` / `stm32wb`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `ble`, `nimble`, `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `nucleo-wb55rg` (`arm/stm32wb`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s). Key symbols: `[board.h:stm32_board_initialize]` Public declaration `stm32_board_initialize()`, `[board.h:DMAMAP_SPI1_RX]` Hardware/board configuration macros (`DMAMAP_SPI1_RX`, `DMAMAP_SPI1_TX`, `DMAMAP_USART1_RX`, `DMAMAP_ADC1`, `GPIO_USART1_RX`, `GPIO_USART1_TX` (+43 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `nucleo-wb55rg` (`arm/stm32wb`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
