# `stm32f3discovery/include` Component (`boards/arm/stm32f3/stm32f3discovery/include`)

## Overview
Board-level public headers (`include`) for `stm32f3discovery` (`arm/stm32f3`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_CFGR_PLLSRC` (+64 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh stm32f3discovery:nsh && make`
