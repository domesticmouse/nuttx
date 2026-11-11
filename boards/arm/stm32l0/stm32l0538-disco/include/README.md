# `stm32l0538-disco/include` Component (`boards/arm/stm32l0/stm32l0538-disco/include`)

## Overview
Board-level public headers (`include`) for `stm32l0538-disco` (`arm/stm32l0`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_HSEBYP_ENABLE`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_LSE_FREQUENCY` (+43 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh stm32l0538-disco:nsh && make`
