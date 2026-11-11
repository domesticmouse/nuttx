# `frdm-mcxn236` Board Support Package (`boards/arm/mcx-nxxx/frdm-mcxn236`)

## Overview
Board Support Package (BSP) blueprint for `frdm-mcxn236` (`arm` / `mcx-nxxx`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `frdm-mcxn236` (`arm/mcx-nxxx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:nxxx_boardinitialize]` Public declaration `nxxx_boardinitialize()`, `[board.h:PORT_LPUART4_RX]` Hardware/board configuration macros (`PORT_LPUART4_RX`, `PORT_LPUART4_TX`, `PORT_LPI2C0_SCL`, `PORT_LPI2C0_SDA`).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `frdm-mcxn236` (`arm/mcx-nxxx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 3 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
