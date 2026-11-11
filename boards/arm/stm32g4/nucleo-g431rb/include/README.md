# `nucleo-g431rb/include` Component (`boards/arm/stm32g4/nucleo-g431rb/include`)

## Overview
Board-level public headers (`include`) for `nucleo-g431rb` (`arm/stm32g4`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_PLLCFGR_PLLSRC`, `STM32_PLLCFGR_PLLCFG` (+72 more))

## Invariants
- `[board.h:#error]` Compile-time guard: `For now FDCAN supported only if HSE enabled`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh nucleo-g431rb:nsh && make`
