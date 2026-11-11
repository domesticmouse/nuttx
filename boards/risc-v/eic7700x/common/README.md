# `common` Board Support Package (`boards/risc-v/eic7700x/common`)

## Overview
Board Support Package (BSP) blueprint for `common` (`risc-v` / `eic7700x`). Coordinates board initialization, headers, and tooling across `src, tools`.

## Subdirectories & Boundaries
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `common` (`risc-v/eic7700x`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 1 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[eic7700x_boot.c:board_late_initialize]` Public function `board_late_initialize()`.
- [`tools`](./tools/README.md) - Board support component `tools` for `common` (`risc-v/eic7700x`), containing 1 source/script file(s) (`mkimage.sh`). Key symbols: `[mkimage.sh]` Shell script entry point `mkimage.sh`.
