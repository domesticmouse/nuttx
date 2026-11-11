# `nucleo-h563zi/include` Component (`boards/arm/stm32h5/nucleo-h563zi/include`)

## Overview
Board-level public headers (`include`) for `nucleo-h563zi` (`arm/stm32h5`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:stm32_board_initialize]` Public declaration `stm32_board_initialize()`
- `[board.h:STM32_SYSCLK_FREQUENCY]` Hardware/board configuration macros (`STM32_SYSCLK_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_BOARD_USEHSE`, `STM32_PLLCFG_PLL1CFG` (+111 more))

## Invariants
- `[board.h:#error]` Compile-time guard: `This board config requires HSE to use the USB HOST.`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh nucleo-h563zi:nsh && make`
