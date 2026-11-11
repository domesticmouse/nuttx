# `stm32ldiscovery/include` Component (`boards/arm/stm32l1/stm32ldiscovery/include`)

## Overview
Board-level public headers (`include`) for `stm32ldiscovery` (`arm/stm32l1`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:stm32_slcd_initialize]` Public declaration `stm32_slcd_initialize()`
- `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_HSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_MSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_LSE_FREQUENCY` (+45 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh stm32ldiscovery:nsh && make`
