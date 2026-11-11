# `zkit-arm-1769` Board Support Package (`boards/arm/lpc17xx_40xx/zkit-arm-1769`)

## Overview
Board Support Package (BSP) blueprint for `zkit-arm-1769` (`arm` / `lpc17xx_40xx`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `hello`, `nsh`, `nxhello`, `thttpd`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `zkit-arm-1769` (`arm/lpc17xx_40xx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:lpc17_40_led]` Public declaration `lpc17_40_led()`, `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `BOARD_OSCCLK_FREQUENCY`, `BOARD_RTCCLK_FREQUENCY`, `BOARD_INTRCOSC_FREQUENCY`, `LPC17_40_CCLK`, `CONFIG_LPC17_40_MAINOSC` (+56 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `zkit-arm-1769` (`arm/lpc17xx_40xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 11 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
