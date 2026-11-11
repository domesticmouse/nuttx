# `stm32h745i-disco/include` Component (`boards/arm/stm32h7/stm32h745i-disco/include`)

## Overview
Board-level public headers (`include`) for `stm32h745i-disco` (`arm/stm32h7`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:STM32_HSI_FREQUENCY]` Hardware/board configuration macros (`STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_BOARD_USEHSE`, `STM32_HSEBYP_ENABLE` (+177 more))

## Invariants
- `[board.h:#error]` Compile-time guard: `FMC SDRAM settings need to be adjusted for a higher FMC_SDCLK frequency`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh stm32h745i-disco:nsh && make`
