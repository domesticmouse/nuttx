# `stm32butterfly2/include` Component (`boards/arm/stm32f1/stm32butterfly2/include`)

## Overview
Board-level public headers (`include`) for `stm32butterfly2` (`arm/stm32f1`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_PLL_PREDIV2` (+77 more))

## Invariants
- `[board.h:#error]` Compile-time guard: `CONFIG_STM32_ADC2 is not supported`
- `[board.h:#error]` Compile-time guard: `CONFIG_STM32_SPI2 is not supported`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh stm32butterfly2:nsh && make`
