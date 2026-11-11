# `emw3162/include` Component (`boards/arm/stm32f2/emw3162/include`)

## Overview
Board-level public headers (`include`) for `emw3162` (`arm/stm32f2`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_PLLCFG_PLLM` (+34 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh emw3162:nsh && make`
