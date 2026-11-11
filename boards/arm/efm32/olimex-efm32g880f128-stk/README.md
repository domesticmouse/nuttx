# `olimex-efm32g880f128-stk` Board Support Package (`boards/arm/efm32/olimex-efm32g880f128-stk`)

## Overview
Board Support Package (BSP) blueprint for `olimex-efm32g880f128-stk` (`arm` / `efm32`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `olimex-efm32g880f128-stk` (`arm/efm32`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_HAVE_HFXO]` Hardware/board configuration macros (`BOARD_HAVE_HFXO`, `BOARD_HAVE_LFXO`, `BOARD_HFRCO_FREQUENCY`, `BOARD_HFXO_FREQUENCY`, `BOARD_LFRCO_FREQUENCY`, `BOARD_LFXO_FREQUENCY` (+48 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `olimex-efm32g880f128-stk` (`arm/efm32`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 3 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[efm32g880f128-stk.h:GPIO_BUTTON_1]` Hardware/board configuration macros (`GPIO_BUTTON_1`, `GPIO_BUTTON_2`, `GPIO_BUTTON_3`, `GPIO_BUTTON_4`, `GPIO_IRQ_BUTTON_1`, `GPIO_IRQ_BUTTON_2` (+2 more)).
