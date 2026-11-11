# `tm4c123g-launchpad` Board Support Package (`boards/arm/tiva/tm4c123g-launchpad`)

## Overview
Board Support Package (BSP) blueprint for `tm4c123g-launchpad` (`arm` / `tiva`). Coordinates board initialization, headers, and tooling across `include, src, tools`. Includes build configurations: `mcp2515`, `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `tm4c123g-launchpad` (`arm/tiva`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:SYSCON_RCC_XTAL]` Hardware/board configuration macros (`SYSCON_RCC_XTAL`, `XTAL_FREQUENCY`, `SYSCON_RCC_OSCSRC`, `SYSCON_RCC2_OSCSRC`, `OSCSRC_FREQUENCY`, `TIVA_SYSDIV` (+29 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `tm4c123g-launchpad` (`arm/tiva`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 11 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
- [`tools`](./tools/README.md) - Board support component `tools` for `tm4c123g-launchpad` (`arm/tiva`), containing 1 source/script file(s) (`oocd.sh`). Key symbols: `[oocd.sh]` Shell script entry point `oocd.sh`.
