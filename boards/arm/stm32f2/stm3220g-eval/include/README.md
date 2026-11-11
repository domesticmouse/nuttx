# `stm3220g-eval/include` Component (`boards/arm/stm32f2/stm3220g-eval/include`)

## Overview
Board-level public headers (`include`) for `stm3220g-eval` (`arm/stm32f2`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:stm3220g_lcdclear]` Public declaration `stm3220g_lcdclear()`
- `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_PLLCFG_PLLM` (+151 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh stm3220g-eval:nsh && make`
