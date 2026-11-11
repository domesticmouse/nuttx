# `n32h762iil7/include` Component (`boards/arm/n32h7/n32h762iil7/include`)

## Overview
Board-level public headers (`include`) for `n32h762iil7` (`arm/n32h7`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:N32_BOARD_XTAL]` Hardware/board configuration macros (`N32_BOARD_XTAL`, `N32_HSI_FREQUENCY`, `N32_MSI_FREQUENCY`, `N32_LSI_FREQUENCY`, `N32_HSE_FREQUENCY`, `N32_LSE_FREQUENCY` (+85 more))

## Invariants
- `[board.h:#error]` Compile-time guard: `PLL configuration not supported`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh n32h762iil7:nsh && make`
