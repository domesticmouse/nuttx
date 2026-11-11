# `at32f437-mini/include` Component (`boards/arm/at32/at32f437-mini/include`)

## Overview
Board-level public headers (`include`) for `at32f437-mini` (`arm/at32`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:AT32_BOARD_XTAL]` Hardware/board configuration macros (`AT32_BOARD_XTAL`, `AT32_HSI_FREQUENCY`, `AT32_LSI_FREQUENCY`, `AT32_HSE_FREQUENCY`, `AT32_LSE_FREQUENCY`, `AT32_PLLCFG_PLLM` (+71 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh at32f437-mini:nsh && make`
