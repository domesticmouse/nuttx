# `fire-stm32v2/include` Component (`boards/arm/stm32f1/fire-stm32v2/include`)

## Overview
Board-level public headers (`include`) for `fire-stm32v2` (`arm/stm32f1`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_CFGR_PLLSRC` (+59 more))

## Invariants
- `[board.h:#error]` Compile-time guard: `SPI1 requires CONFIG_STM32_SPI1_REMAP=n`
- `[board.h:#error]` Compile-time guard: `SPI1 requires CONFIG_STM32_I2C1_REMAP=n`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh fire-stm32v2:nsh && make`
