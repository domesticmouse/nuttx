# `olimex-lpc1766stk` Board Support Package (`boards/arm/lpc17xx_40xx/olimex-lpc1766stk`)

## Overview
Board Support Package (BSP) blueprint for `olimex-lpc1766stk` (`arm` / `lpc17xx_40xx`). Coordinates board initialization, headers, and tooling across `include, src, tools`. Includes build configurations: `ftpc`, `hidkbd`, `hidmouse`, `nettest`, `nsh`, `slip-httpd` (+5 more).

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `olimex-lpc1766stk` (`arm/lpc17xx_40xx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `BOARD_OSCCLK_FREQUENCY`, `BOARD_RTCCLK_FREQUENCY`, `BOARD_INTRCOSC_FREQUENCY`, `LPC17_40_CCLK`, `CONFIG_LPC17_40_MAINOSC` (+67 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `olimex-lpc1766stk` (`arm/lpc17xx_40xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
- [`tools`](./tools/README.md) - Board support component `tools` for `olimex-lpc1766stk` (`arm/lpc17xx_40xx`), containing 1 source/script file(s) (`oocd.sh`). Key symbols: `[oocd.sh]` Shell script entry point `oocd.sh`.
