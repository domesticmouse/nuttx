# `common` Board Support Package (`boards/arm/nrf52/common`)

## Overview
Board Support Package (BSP) blueprint for `common` (`arm` / `nrf52`). Coordinates board initialization, headers, and tooling across `include, src`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `common` (`arm/nrf52`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 5 header file(s). Key symbols: `[nrf52_ieee802154.h:nrf52_ieee802154_initialize]` Public declaration `nrf52_ieee802154_initialize()`, `[nrf52_lsm9ds1.h:nrf52_lsm9ds1_initialize]` Public declaration `nrf52_lsm9ds1_initialize()`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `common` (`arm/nrf52`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
