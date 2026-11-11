# `common` Board Support Package (`boards/risc-v/rp23xx-rv/common`)

## Overview
Board Support Package (BSP) blueprint for `common` (`risc-v` / `rp23xx-rv`). Coordinates board initialization, headers, and tooling across `include, src`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `common` (`risc-v/rp23xx-rv`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 5 header file(s). Key symbols: `[rp23xx_common_bringup.h:rp23xx_common_bringup]` Public declaration `rp23xx_common_bringup()`, `[rp23xx_common_initialize.h:rp23xx_common_earlyinitialize]` Public declaration `rp23xx_common_earlyinitialize()`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `common` (`risc-v/rp23xx-rv`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 12 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
