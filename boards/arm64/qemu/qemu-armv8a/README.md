# `qemu-armv8a` Board Support Package (`boards/arm64/qemu/qemu-armv8a`)

## Overview
Board Support Package (BSP) blueprint for `qemu-armv8a` (`arm64` / `qemu`). Coordinates board initialization, headers, and tooling across `configs, include, src`. Includes build configurations: `citest`, `citest_smp`, `fastboot`, `fb`, `gdbstub`, `knsh` (+17 more).

## Subdirectories & Boundaries
- [`configs`](./configs/README.md) - Intermediate blueprint for `qemu-armv8a/configs` (`arm64/qemu`), grouping `citest, citest_smp`.
- [`include`](./include/README.md) - Board-level public headers (`include`) for `qemu-armv8a` (`arm64/qemu`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s). Key symbols: `[board.h]` Board header declarations `board.h`, `[board_memorymap.h]` Board header declarations `board_memorymap.h`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `qemu-armv8a` (`arm64/qemu`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
