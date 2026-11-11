# `linum-stm32h753bi/include` Component (`boards/arm/stm32h7/linum-stm32h753bi/include`)

## Overview
Board-level public headers (`include`) for `linum-stm32h753bi` (`arm/stm32h7`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:STM32_HSI_FREQUENCY]` Hardware/board configuration macros (`STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_BOARD_USEHSE`, `STM32_PLLCFG_PLLSRC` (+200 more))

## Invariants
- `[board.h:#error]` Compile-time guard: `FMC SDRAM settings need to be adjusted for a higher FMC_SDCLK frequency`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh linum-stm32h753bi:nsh && make`
