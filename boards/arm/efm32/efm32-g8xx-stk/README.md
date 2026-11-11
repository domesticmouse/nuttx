# `efm32-g8xx-stk` Board Support Package (`boards/arm/efm32/efm32-g8xx-stk`)

## Overview
Board Support Package (BSP) blueprint for `efm32-g8xx-stk` (`arm` / `efm32`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `efm32-g8xx-stk` (`arm/efm32`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_HAVE_HFXO]` Hardware/board configuration macros (`BOARD_HAVE_HFXO`, `BOARD_HAVE_LFXO`, `BOARD_HFRCO_FREQUENCY`, `BOARD_HFXO_FREQUENCY`, `BOARD_LFRCO_FREQUENCY`, `BOARD_LFXO_FREQUENCY` (+35 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `efm32-g8xx-stk` (`arm/efm32`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[efm32-g8xx-stk.h:GPIO_BC_EN]` Hardware/board configuration macros (`GPIO_BC_EN`, `GPIO_LED0`, `GPIO_LED1`, `GPIO_LED2`, `GPIO_LED3`).
