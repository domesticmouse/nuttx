# `b-g431b-esc1/include` Component (`boards/arm/stm32g4/b-g431b-esc1/include`)

## Overview
Board-level public headers (`include`) for `b-g431b-esc1` (`arm/stm32g4`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_PLLCFGR_PLLSRC`, `STM32_PLLCFGR_PLLCFG` (+81 more))

## Invariants
- `[board.h:#error]` Compile-time guard: `For now FDCAN supported only if HSE enabled`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh b-g431b-esc1:nsh && make`
