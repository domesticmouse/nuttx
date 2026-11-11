# `olimex-strp711/include` Component (`boards/arm/str71x/olimex-strp711/include`)

## Overview
Board-level public headers (`include`) for `olimex-strp711` (`arm/str71x`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:STR71X_RCCU_MAIN_OSC]` Hardware/board configuration macros (`STR71X_RCCU_MAIN_OSC`, `STR71X_RCCU_RTC_OSC`, `STR71X_PCU_HCLK_OSC`, `STR71X_PLL1OUT_MUL`, `STR71X_PLL1OUT_DIV`, `STR71X_APB1_DIV` (+14 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh olimex-strp711:nsh && make`
