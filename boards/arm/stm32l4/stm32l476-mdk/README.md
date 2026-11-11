# `stm32l476-mdk` Board Support Package (`boards/arm/stm32l4/stm32l476-mdk`)

## Overview
Board Support Package (BSP) blueprint for `stm32l476-mdk` (`arm` / `stm32l4`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `stm32l476-mdk` (`arm/stm32l4`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s). Key symbols: `[board.h:stm32_board_initialize]` Public declaration `stm32_board_initialize()`, `[board.h:GPIO_USART1_CTS]` Hardware/board configuration macros (`GPIO_USART1_CTS`, `GPIO_USART1_RTS`, `GPIO_USART1_RX`, `GPIO_USART1_TX`, `GPIO_USART2_CTS`, `GPIO_USART2_RTS` (+36 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `stm32l476-mdk` (`arm/stm32l4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
