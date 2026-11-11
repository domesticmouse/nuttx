# `lx_cpu` Board Support Package (`boards/arm/lpc17xx_40xx/lx_cpu`)

## Overview
Board Support Package (BSP) blueprint for `lx_cpu` (`arm` / `lpc17xx_40xx`). Coordinates board initialization, headers, and tooling across `include, src, tools`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `lx_cpu` (`arm/lpc17xx_40xx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:nuttx_ulan_get_chip_data]` Public declaration `nuttx_ulan_get_chip_data()`, `[board.h:nuttx_ulan_chip_data_s]` Type definition `nuttx_ulan_chip_data_s`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `lx_cpu` (`arm/lpc17xx_40xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 12 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[lx_cpu.h:lx_cpu_bringup]` Public declaration `lx_cpu_bringup()`.
- [`tools`](./tools/README.md) - Board support component `tools` for `lx_cpu` (`arm/lpc17xx_40xx`), containing 1 source/script file(s) (`oocd.sh`). Key symbols: `[oocd.sh]` Shell script entry point `oocd.sh`.
