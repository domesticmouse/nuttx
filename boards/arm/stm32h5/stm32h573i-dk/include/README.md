# `stm32h573i-dk/include` Component (`boards/arm/stm32h5/stm32h573i-dk/include`)

## Overview
Board-level public headers (`include`) for `stm32h573i-dk` (`arm/stm32h5`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:STM32_BOARD_USEHSE]` Hardware/board configuration macros (`STM32_BOARD_USEHSE`, `STM32_HSEBYP_ENABLE`, `STM32_HSEEXT_ENABLE`, `STM32_HSE_FREQUENCY`, `STM32_HSI_FREQUENCY`, `STM32_CSI_FREQUENCY` (+67 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh stm32h573i-dk:nsh && make`
