# `flipperzero` Board Support Package (`boards/arm/stm32wb/flipperzero`)

## Overview
Board Support Package (BSP) blueprint for `flipperzero` (`arm` / `stm32wb`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `flipperzero` (`arm/stm32wb`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s). Key symbols: `[board.h:stm32_board_initialize]` Public declaration `stm32_board_initialize()`, `[board.h:GPIO_USART1_TX]` Hardware/board configuration macros (`GPIO_USART1_TX`, `GPIO_USART1_RX`, `GPIO_SPI2_SCK`, `GPIO_SPI2_MISO`, `GPIO_SPI2_MOSI`, `LED_STARTED` (+18 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `flipperzero` (`arm/stm32wb`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
