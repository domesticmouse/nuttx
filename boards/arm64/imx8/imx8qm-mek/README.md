# `imx8qm-mek` Board Support Package (`boards/arm64/imx8/imx8qm-mek`)

## Overview
Board Support Package (BSP) blueprint for `imx8qm-mek` (`arm64` / `imx8`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `imx8qm-mek` (`arm64/imx8`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s). Key symbols: `[board.h]` Board header declarations `board.h`, `[board_memorymap.h]` Board header declarations `board_memorymap.h`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `imx8qm-mek` (`arm64/imx8`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 3 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
