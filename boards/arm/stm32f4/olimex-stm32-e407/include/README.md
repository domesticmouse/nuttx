# `olimex-stm32-e407/include` Component (`boards/arm/stm32f4/olimex-stm32-e407/include`)

## Overview
Board-level public headers (`include`) for `olimex-stm32-e407` (`arm/stm32f4`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_PLLCFG_PLLM` (+72 more))

## Invariants
- `[board.h:#error]` Compile-time guard: `CONFIG_STM32_RMII must be defined`
- `[board.h:#error]` Compile-time guard: `CONFIG_STM32_RMII_EXTCLK must be defined`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh olimex-stm32-e407:nsh && make`
