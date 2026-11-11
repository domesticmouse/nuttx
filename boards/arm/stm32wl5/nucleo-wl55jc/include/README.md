# `nucleo-wl55jc/include` Component (`boards/arm/stm32wl5/nucleo-wl55jc/include`)

## Overview
Board-level public headers (`include`) for `nucleo-wl55jc` (`arm/stm32wl5`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:stm32_board_initialize]` Public declaration `stm32_board_initialize()`
- `[board.h:STM32_XTAL_FREQ]` Hardware/board configuration macros (`STM32_XTAL_FREQ`, `STM32_BOARD_USEHSE`, `STM32_BOARD_USETCXO`, `STM32_LSI_FREQUENCY`, `STM32_PLLCFG_PLLM`, `STM32_PLLCFG_PLLP` (+51 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh nucleo-wl55jc:nsh && make`
