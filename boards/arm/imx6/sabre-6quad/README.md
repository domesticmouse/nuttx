# `sabre-6quad` Board Support Package (`boards/arm/imx6/sabre-6quad`)

## Overview
Board Support Package (BSP) blueprint for `sabre-6quad` (`arm` / `imx6`). Coordinates board initialization, headers, and tooling across `configs, include, src`. Includes build configurations: `citest`, `coredump`, `elf`, `knsh`, `knsh_smp`, `libcxx` (+9 more).

## Subdirectories & Boundaries
- [`configs`](./configs/README.md) - Intermediate blueprint for `sabre-6quad/configs` (`arm/imx6`), grouping `citest`.
- [`include`](./include/README.md) - Board-level public headers (`include`) for `sabre-6quad` (`arm/imx6`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s). Key symbols: `[board.h:BOARD_CPUXTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_CPUXTAL_FREQUENCY`, `BAORD_RTCXTAL_FREQUENCY`, `BOARD_CPU_FREQUENCY`, `BOARD_LED`, `BOARD_NLEDS`, `BOARD_LED_BIT` (+10 more)), `[board_memorymap.h]` Board header declarations `board_memorymap.h`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `sabre-6quad` (`arm/imx6`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
