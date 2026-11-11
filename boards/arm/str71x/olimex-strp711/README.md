# `olimex-strp711` Board Support Package (`boards/arm/str71x/olimex-strp711`)

## Overview
Board Support Package (BSP) blueprint for `olimex-strp711` (`arm` / `str71x`). Coordinates board initialization, headers, and tooling across `include, scripts, src`. Includes build configurations: `nettest`, `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `olimex-strp711` (`arm/str71x`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:STR71X_RCCU_MAIN_OSC]` Hardware/board configuration macros (`STR71X_RCCU_MAIN_OSC`, `STR71X_RCCU_RTC_OSC`, `STR71X_PCU_HCLK_OSC`, `STR71X_PLL1OUT_MUL`, `STR71X_PLL1OUT_DIV`, `STR71X_APB1_DIV` (+14 more)).
- [`scripts`](./scripts/README.md) - Board support component `scripts` for `olimex-strp711` (`arm/str71x`), containing 1 source/script file(s) (`oocd.sh`). Key symbols: `[oocd.sh]` Shell script entry point `oocd.sh`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `olimex-strp711` (`arm/str71x`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[str71_boardinit.c:board_late_initialize]` Public function `board_late_initialize()`.
