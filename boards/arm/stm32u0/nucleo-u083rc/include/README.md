# `nucleo-u083rc/include` Component (`boards/arm/stm32u0/nucleo-u083rc/include`)

## Overview
Board-level public headers (`include`) for `nucleo-u083rc` (`arm/stm32u0`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_PLLCFG_PLLSRC` (+50 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh nucleo-u083rc:nsh && make`
