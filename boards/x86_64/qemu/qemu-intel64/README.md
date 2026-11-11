# `qemu-intel64` Board Support Package (`boards/x86_64/qemu/qemu-intel64`)

## Overview
Board Support Package (BSP) blueprint for `qemu-intel64` (`x86_64` / `qemu`). Coordinates board initialization, headers, and tooling across `configs, include, src`. Includes build configurations: `citest_smp`, `earlyfb`, `fb`, `jumbo`, `knsh_romfs`, `knsh_romfs_pci` (+9 more).

## Subdirectories & Boundaries
- [`configs`](./configs/README.md) - Intermediate blueprint for `qemu-intel64/configs` (`x86_64/qemu`), grouping `citest_smp`.
- [`include`](./include/README.md) - Board-level public headers (`include`) for `qemu-intel64` (`x86_64/qemu`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:PIT_CLOCK]` Hardware/board configuration macros (`PIT_CLOCK`).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `qemu-intel64` (`x86_64/qemu`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 9 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
