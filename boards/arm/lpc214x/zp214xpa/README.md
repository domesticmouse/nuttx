# `zp214xpa` Board Support Package (`boards/arm/lpc214x/zp214xpa`)

## Overview
Board Support Package (BSP) blueprint for `zp214xpa` (`arm` / `lpc214x`). Coordinates board initialization, headers, and tooling across `include, src, tools`. Includes build configurations: `nsh`, `nxlines`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `zp214xpa` (`arm/lpc214x`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:LPC214X_FOSC]` Hardware/board configuration macros (`LPC214X_FOSC`, `LPC214X_PLL_M`, `LPC214X_PLL_P`, `LPC214X_APB_DIV`, `LPC214X_USBPLL_M`, `LPC214X_USBPLL_P`).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `zp214xpa` (`arm/lpc214x`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 3 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[lpc2148_boardinit.c:board_late_initialize]` Public function `board_late_initialize()`.
- [`tools`](./tools/README.md) - Board support component `tools` for `zp214xpa` (`arm/lpc214x`), containing 1 source/script file(s) (`oocd.sh`). Key symbols: `[oocd.sh]` Shell script entry point `oocd.sh`.
