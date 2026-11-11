# `nucleo-l476rg` Board Support Package (`boards/arm/stm32l4/nucleo-l476rg`)

## Overview
Board Support Package (BSP) blueprint for `nucleo-l476rg` (`arm` / `stm32l4`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `nxdemo`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `nucleo-l476rg` (`arm/stm32l4`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s). Key symbols: `[board.h:DMACHAN_SDMMC]` Hardware/board configuration macros (`DMACHAN_SDMMC`, `DMACHAN_SPI1_RX`, `DMACHAN_SPI1_TX`, `DMACHAN_USART1_RX`, `ADC1_DMA_CHAN`, `ADC2_DMA_CHAN` (+53 more)), `[nucleo-l476rg.h:HSI_CLOCK_CONFIG]` Hardware/board configuration macros (`HSI_CLOCK_CONFIG`, `HSE_CLOCK_CONFIG`, `MSI_CLOCK_CONFIG`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_LSE_FREQUENCY` (+42 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `nucleo-l476rg` (`arm/stm32l4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 24 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
