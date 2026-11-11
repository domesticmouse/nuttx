# `common` Board Support Package (`boards/arm/cxd56xx/common`)

## Overview
Board Support Package (BSP) blueprint for `common` (`arm` / `cxd56xx`). Coordinates board initialization, headers, and tooling across `src`.

## Subdirectories & Boundaries
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `common` (`arm/cxd56xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 43 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[cxd56_ak09912_i2c.c:board_ak09912_initialize]` Public function `board_ak09912_initialize()`.
