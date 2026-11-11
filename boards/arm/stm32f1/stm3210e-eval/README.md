# `stm3210e-eval` Board Support Package (`boards/arm/stm32f1/stm3210e-eval`)

## Overview
Board Support Package (BSP) blueprint for `stm3210e-eval` (`arm` / `stm32f1`). Coordinates board initialization, headers, and tooling across `include, src, tools`. Includes build configurations: `composite`, `nsh`, `nsh2`, `nx`, `nxterm`, `pm` (+2 more).

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `stm3210e-eval` (`arm/stm32f1`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:stm3210e_lcdclear]` Public declaration `stm3210e_lcdclear()`, `[board.h:stm32_lm75initialize]` Public declaration `stm32_lm75initialize()`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `stm3210e-eval` (`arm/stm32f1`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 24 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
- [`tools`](./tools/README.md) - Board support component `tools` for `stm3210e-eval` (`arm/stm32f1`), containing 1 source/script file(s) (`oocd.sh`). Key symbols: `[oocd.sh]` Shell script entry point `oocd.sh`.
