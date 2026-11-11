# `mcu123-lpc214x` Board Support Package (`boards/arm/lpc214x/mcu123-lpc214x`)

## Overview
Board Support Package (BSP) blueprint for `mcu123-lpc214x` (`arm` / `lpc214x`). Coordinates board initialization, headers, and tooling across `include, scripts, src`. Includes build configurations: `composite`, `nsh`, `usbmsc`, `usbserial`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `mcu123-lpc214x` (`arm/lpc214x`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:LPC214X_FOSC]` Hardware/board configuration macros (`LPC214X_FOSC`, `LPC214X_PLL_M`, `LPC214X_PLL_P`, `LPC214X_APB_DIV`, `LPC214X_USBPLL_M`, `LPC214X_USBPLL_P` (+8 more)).
- [`scripts`](./scripts/README.md) - Board support component `scripts` for `mcu123-lpc214x` (`arm/lpc214x`), containing 1 source/script file(s) (`lpc21isp.sh`). Key symbols: `[lpc21isp.sh]` Shell script entry point `lpc21isp.sh`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `mcu123-lpc214x` (`arm/lpc214x`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[lpc2148_boardinit.c:board_late_initialize]` Public function `board_late_initialize()`.
