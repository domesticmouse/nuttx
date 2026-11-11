# `shenzhou` Board Support Package (`boards/arm/stm32f1/shenzhou`)

## Overview
Board Support Package (BSP) blueprint for `shenzhou` (`arm` / `stm32f1`). Coordinates board initialization, headers, and tooling across `include, src, tools`. Includes build configurations: `nsh`, `nxwm`, `thttpd`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `shenzhou` (`arm/stm32f1`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:stm32_lcdclear]` Public declaration `stm32_lcdclear()`, `[board.h:up_relaysinit]` Public declaration `up_relaysinit()`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `shenzhou` (`arm/stm32f1`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 17 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
- [`tools`](./tools/README.md) - Board support component `tools` for `shenzhou` (`arm/stm32f1`), containing 1 source/script file(s) (`oocd.sh`). Key symbols: `[oocd.sh]` Shell script entry point `oocd.sh`.
