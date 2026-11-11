# `stm32f401rc-rs485/include` Component (`boards/arm/stm32f4/stm32f401rc-rs485/include`)

## Overview
Board-level public headers (`include`) for `stm32f401rc-rs485` (`arm/stm32f4`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:STM32_HSI_FREQUENCY]` Hardware/board configuration macros (`STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_BOARD_USEHSI`, `STM32_PLLCFG_PLLM`, `STM32_PLLCFG_PLLN`, `STM32_PLLCFG_PLLP` (+102 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh stm32f401rc-rs485:nsh && make`
