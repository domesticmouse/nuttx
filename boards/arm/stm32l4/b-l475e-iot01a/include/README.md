# `b-l475e-iot01a/include` Component (`boards/arm/stm32l4/b-l475e-iot01a/include`)

## Overview
Board-level public headers (`include`) for `b-l475e-iot01a` (`arm/stm32l4`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s).

## Interface
- `[b-l475e-iot01a_clock.h:HSI_CLOCK_CONFIG]` Hardware/board configuration macros (`HSI_CLOCK_CONFIG`, `HSE_CLOCK_CONFIG`, `MSI_CLOCK_CONFIG`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_LSE_FREQUENCY` (+43 more))
- `[board.h:BOARD_LED1]` Hardware/board configuration macros (`BOARD_LED1`, `BOARD_LED2`, `BOARD_NLEDS`, `BOARD_LED1_BIT`, `BOARD_LED2_BIT`, `LED_STARTED` (+42 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh b-l475e-iot01a:nsh && make`
