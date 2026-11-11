# `ntosd-dm320` Board Support Package (`boards/arm/dm320/ntosd-dm320`)

## Overview
Board Support Package (BSP) blueprint for `ntosd-dm320` (`arm` / `dm320`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nettest`, `nsh`, `poll`, `udp`, `webserver`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `ntosd-dm320` (`arm/dm320`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:DM320_ARM_CLOCK]` Hardware/board configuration macros (`DM320_ARM_CLOCK`, `DM320_SDR_CLOCK`, `DM320_DSP_CLOCK`, `DM320_AXL_CLOCK`, `DM320_AHB_CLOCK`, `CONFIG_DM320_UARTPPLIN` (+40 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `ntosd-dm320` (`arm/dm320`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 3 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[dm320_boardinit.c:board_late_initialize]` Public function `board_late_initialize()`.
