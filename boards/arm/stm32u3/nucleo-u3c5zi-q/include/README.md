# `nucleo-u3c5zi-q/include` Component (`boards/arm/stm32u3/nucleo-u3c5zi-q/include`)

## Overview
Board-level public headers (`include`) for `nucleo-u3c5zi-q` (`arm/stm32u3`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:stm32_board_initialize]` Public declaration `stm32_board_initialize()`
- `[board.h:STM32_BOARD_USEMSIS]` Hardware/board configuration macros (`STM32_BOARD_USEMSIS`, `STM32_RCC_ICSCR1_MSISSEL`, `STM32_RCC_ICSCR1_MSISDIV`, `STM32_RCC_CFGR4_BOOSTSEL`, `STM32_RCC_CFGR4_BOOSTDIV`, `STM32_PWR_CR3_REGSEL` (+46 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh nucleo-u3c5zi-q:nsh && make`
