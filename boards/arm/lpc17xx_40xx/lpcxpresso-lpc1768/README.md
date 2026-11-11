# `lpcxpresso-lpc1768` Board Support Package (`boards/arm/lpc17xx_40xx/lpcxpresso-lpc1768`)

## Overview
Board Support Package (BSP) blueprint for `lpcxpresso-lpc1768` (`arm` / `lpc17xx_40xx`). Coordinates board initialization, headers, and tooling across `include, src, tools`. Includes build configurations: `dhcpd`, `nsh`, `nx`, `thttpd`, `usbmsc`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `lpcxpresso-lpc1768` (`arm/lpc17xx_40xx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `BOARD_OSCCLK_FREQUENCY`, `BOARD_RTCCLK_FREQUENCY`, `BOARD_INTRCOSC_FREQUENCY`, `LPC17_40_CCLK`, `CONFIG_LPC17_40_MAINOSC` (+38 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `lpcxpresso-lpc1768` (`arm/lpc17xx_40xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 9 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
- [`tools`](./tools/README.md) - Board support component `tools` for `lpcxpresso-lpc1768` (`arm/lpc17xx_40xx`), containing 1 source/script file(s) (`flash.sh`). Key symbols: `[flash.sh]` Shell script entry point `flash.sh`.
