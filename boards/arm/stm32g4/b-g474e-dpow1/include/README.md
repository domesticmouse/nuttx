# `b-g474e-dpow1/include` Component (`boards/arm/stm32g4/b-g474e-dpow1/include`)

## Overview
Board-level public headers (`include`) for `b-g474e-dpow1` (`arm/stm32g4`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:STM32_HSI_FREQUENCY]` Hardware/board configuration macros (`STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_PLLCFGR_PLLSRC`, `STM32_PLLCFGR_PLLCFG`, `STM32_PLLCFGR_PLLN`, `STM32_PLLCFGR_PLLM` (+82 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh b-g474e-dpow1:nsh && make`
