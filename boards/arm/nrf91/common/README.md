# `common` Board Support Package (`boards/arm/nrf91/common`)

## Overview
Board Support Package (BSP) blueprint for `common` (`arm` / `nrf91`). Coordinates board initialization, headers, and tooling across `include, src`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `common` (`arm/nrf91`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 6 header file(s). Key symbols: `[nrf91_adxl362.h:nrf91_adxl362_init]` Public declaration `nrf91_adxl362_init()`, `[nrf91_adxl372.h:nrf91_adxl372_init]` Public declaration `nrf91_adxl372_init()`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `common` (`arm/nrf91`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
