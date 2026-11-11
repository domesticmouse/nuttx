# `viewtool-stm32f107/include` Component (`boards/arm/stm32f1/viewtool-stm32f107/include`)

## Overview
Board-level public headers (`include`) for `viewtool-stm32f107` (`arm/stm32f1`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 3 header file(s).

## Interface
- `[board-stm32f103vct6.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_CFGR_PLLSRC`, `STM32_CFGR_PLLXTPRE`, `STM32_CFGR_PLLMUL`, `STM32_PLL_FREQUENCY`, `STM32_SYSCLK_SW` (+18 more))
- `[board-stm32f107vct6.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_PLL_PREDIV2` (+22 more))
- `[board.h:BOARD_LED1]` Hardware/board configuration macros (`BOARD_LED1`, `BOARD_LED2`, `BOARD_LED3`, `BOARD_LED4`, `BOARD_NLEDS`, `BOARD_LED1_BIT` (+49 more))

## Invariants
- `[board.h:#error]` Compile-time guard: `Unrecognized STM32 chip`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh viewtool-stm32f107:nsh && make`
