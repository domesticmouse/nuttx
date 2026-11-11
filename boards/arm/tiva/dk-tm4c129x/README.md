# `dk-tm4c129x` Board Support Package (`boards/arm/tiva/dk-tm4c129x`)

## Overview
Board Support Package (BSP) blueprint for `dk-tm4c129x` (`arm` / `tiva`). Coordinates board initialization, headers, and tooling across `include, src, tools`. Includes build configurations: `ipv6`, `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `dk-tm4c129x` (`arm/tiva`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:tiva_tmp100_initialize]` Public declaration `tiva_tmp100_initialize()`, `[board.h:SYSCON_RCC_XTAL]` Hardware/board configuration macros (`SYSCON_RCC_XTAL`, `XTAL_FREQUENCY`, `PIOSC_FREQUENCY`, `RTCOSC_FREQUENCY`, `LFIOSC_FREQUENCY`, `BOARD_PLL_MINT` (+52 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `dk-tm4c129x` (`arm/tiva`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 10 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[dk-tm4c129x.h:tm4c_ssidev_initialize]` Public declaration `tm4c_ssidev_initialize()`.
- [`tools`](./tools/README.md) - Board support component `tools` for `dk-tm4c129x` (`arm/tiva`), containing 1 source/script file(s) (`oocd.sh`). Key symbols: `[oocd.sh]` Shell script entry point `oocd.sh`.
