# `common` Board Support Package (`boards/arm/rp23xx/common`)

## Overview
Board Support Package (BSP) blueprint for `common` (`arm` / `rp23xx`). Coordinates board initialization, headers, and tooling across `include, src`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `common` (`arm/rp23xx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 6 header file(s). Key symbols: `[rp23xx_common_bringup.h:rp23xx_common_bringup]` Public declaration `rp23xx_common_bringup()`, `[rp23xx_common_initialize.h:rp23xx_common_earlyinitialize]` Public declaration `rp23xx_common_earlyinitialize()`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `common` (`arm/rp23xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 16 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
