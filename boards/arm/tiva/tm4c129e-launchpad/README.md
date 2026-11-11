# `tm4c129e-launchpad` Board Support Package (`boards/arm/tiva/tm4c129e-launchpad`)

## Overview
Board Support Package (BSP) blueprint for `tm4c129e-launchpad` (`arm` / `tiva`). Coordinates board initialization, headers, and tooling across `include, src, tools`. Includes build configurations: `ipv6`, `nsh`, `ostest`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `tm4c129e-launchpad` (`arm/tiva`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:SYSCON_RCC_XTAL]` Hardware/board configuration macros (`SYSCON_RCC_XTAL`, `XTAL_FREQUENCY`, `PIOSC_FREQUENCY`, `RTCOSC_FREQUENCY`, `LFIOSC_FREQUENCY`, `BOARD_PLL_MINT` (+37 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `tm4c129e-launchpad` (`arm/tiva`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 9 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
- [`tools`](./tools/README.md) - Board support component `tools` for `tm4c129e-launchpad` (`arm/tiva`), containing 1 source/script file(s) (`oocd.sh`). Key symbols: `[oocd.sh]` Shell script entry point `oocd.sh`.
