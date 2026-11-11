# `stm3240g-eval/include` Component (`boards/arm/stm32f4/stm3240g-eval/include`)

## Overview
Board-level public headers (`include`) for `stm3240g-eval` (`arm/stm32f4`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:stm3240g_lcdclear]` Public declaration `stm3240g_lcdclear()`
- `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_PLLCFG_PLLM` (+161 more))

## Invariants
- `[board.h:#error]` Compile-time guard: `The STM3240G-EVAL cannot support both CAN and FSMC SRAM`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh stm3240g-eval:nsh && make`
