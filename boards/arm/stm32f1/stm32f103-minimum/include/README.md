# `stm32f103-minimum/include` Component (`boards/arm/stm32f1/stm32f103-minimum/include`)

## Overview
Board-level public headers (`include`) for `stm32f103-minimum` (`arm/stm32f1`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_CFGR_PLLSRC`, `STM32_CFGR_PLLXTPRE`, `STM32_CFGR_PLLMUL`, `STM32_PLL_FREQUENCY`, `STM32_SYSCLK_SW` (+112 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh stm32f103-minimum:nsh && make`
