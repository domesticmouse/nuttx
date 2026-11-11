# `a2g-tc397-5v-tft` Board Support Package (`boards/tricore/tc3xx/a2g-tc397-5v-tft`)

## Overview
Board Support Package (BSP) blueprint for `a2g-tc397-5v-tft` (`tricore` / `tc3xx`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `a2g-tc397-5v-tft` (`tricore/tc3xx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s). Key symbols: `[board.h]` Board header declarations `board.h`, `[board_memorymap.h:BANKA_CORE0_PFLASH_KERNEL_START]` Hardware/board configuration macros (`BANKA_CORE0_PFLASH_KERNEL_START`, `BANKA_CORE0_PFLASH_KERNEL_SIZE`, `BANKA_CORE0_PFLASH_USER_START`, `BANKA_CORE0_PFLASH_USER_SIZE`, `BANKA_CORE1_PFLASH_KERNEL_START`, `BANKA_CORE1_PFLASH_KERNEL_SIZE` (+245 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `a2g-tc397-5v-tft` (`tricore/tc3xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 3 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
