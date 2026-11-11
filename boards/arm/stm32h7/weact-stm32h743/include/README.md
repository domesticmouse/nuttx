# `weact-stm32h743/include` Component (`boards/arm/stm32h7/weact-stm32h743/include`)

## Overview
Board-level public headers (`include`) for `weact-stm32h743` (`arm/stm32h7`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_BOARD_USEHSE` (+103 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh weact-stm32h743:nsh && make`
