# `olimex-stm32-p107/include` Component (`boards/arm/stm32f1/olimex-stm32-p107/include`)

## Overview
Board-level public headers (`include`) for `olimex-stm32-p107` (`arm/stm32f1`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_PLL_PREDIV2` (+51 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh olimex-stm32-p107:nsh && make`
