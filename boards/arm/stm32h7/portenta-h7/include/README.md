# `portenta-h7/include` Component (`boards/arm/stm32h7/portenta-h7/include`)

## Overview
Board-level public headers (`include`) for `portenta-h7` (`arm/stm32h7`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:STM32_HSI_FREQUENCY]` Hardware/board configuration macros (`STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_BOARD_USEHSE`, `STM32_HSEBYP_ENABLE` (+96 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh portenta-h7:jumbo_cm7 && make`
