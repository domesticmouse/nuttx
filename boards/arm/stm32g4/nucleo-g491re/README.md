# `nucleo-g491re` Board Support Package (`boards/arm/stm32g4/nucleo-g491re`)

## Overview
Board Support Package (BSP) blueprint for STMicroelectronics `nucleo-g491re` (`arm` / `stm32g4`). Coordinates board initialization, clock/pin headers, and peripheral bring-up across `include` and `src`. Includes build configuration: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `nucleo-g491re` (`arm/stm32g4`). Defines board-specific clock frequencies (170 MHz PLL from HSI), UART pin mappings, and LED/button definitions in `board.h`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `nucleo-g491re` (`arm/stm32g4`). Provides hardware initialization (`stm32_boot.c`), peripheral bring-up (`stm32_bringup.c`), LED drivers (`stm32_autoleds.c`, `stm32_userleds.c`), and button drivers (`stm32_buttons.c`).
