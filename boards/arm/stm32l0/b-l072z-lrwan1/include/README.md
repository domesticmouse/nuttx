# `b-l072z-lrwan1/include` Component (`boards/arm/stm32l0/b-l072z-lrwan1/include`)

## Overview
Board-level public headers (`include`) for `b-l072z-lrwan1` (`arm/stm32l0`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_CFGR_PLLSRC` (+66 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh b-l072z-lrwan1:nsh && make`
