# `common` Board Support Package (`boards/arm/nrf53/common`)

## Overview
Board Support Package (BSP) blueprint for `common` (`arm` / `nrf53`). Coordinates board initialization, headers, and tooling across `include, src`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `common` (`arm/nrf53`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 8 header file(s). Key symbols: `[nrf53_adxl362.h:nrf53_adxl362_init]` Public declaration `nrf53_adxl362_init()`, `[nrf53_bh1749nuc.h:nrf53_bh1749nuc_init]` Public declaration `nrf53_bh1749nuc_init()`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `common` (`arm/nrf53`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 10 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
