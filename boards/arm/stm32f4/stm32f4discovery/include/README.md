# `stm32f4discovery/include` Component (`boards/arm/stm32f4/stm32f4discovery/include`)

## Overview
Board-level public headers (`include`) for `stm32f4discovery` (`arm/stm32f4`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:board_kmatrix_diag]` Public declaration `board_kmatrix_diag()`
- `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_PLLCFG_PLLM` (+224 more))

## Invariants
- `[board.h:#error]` Compile-time guard: `CONFIG_STM32_RMII must be defined`
- `[board.h:#error]` Compile-time guard: `CONFIG_STM32_RMII_EXTCLK must be defined`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh stm32f4discovery:nsh && make`
