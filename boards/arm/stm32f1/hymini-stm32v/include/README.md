# `hymini-stm32v/include` Component (`boards/arm/stm32f1/hymini-stm32v/include`)

## Overview
Board-level public headers (`include`) for `hymini-stm32v` (`arm/stm32f1`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_CFGR_PLLSRC`, `STM32_CFGR_PLLXTPRE`, `STM32_CFGR_PLLMUL`, `STM32_PLL_FREQUENCY`, `STM32_SYSCLK_SW` (+89 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh hymini-stm32v:nsh && make`
