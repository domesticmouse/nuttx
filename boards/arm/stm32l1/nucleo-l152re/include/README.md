# `nucleo-l152re/include` Component (`boards/arm/stm32l1/nucleo-l152re/include`)

## Overview
Board-level public headers (`include`) for `nucleo-l152re` (`arm/stm32l1`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_CFGR_PLLSRC` (+44 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh nucleo-l152re:nsh && make`
