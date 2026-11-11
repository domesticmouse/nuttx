# `qemu-i486` Board Support Package (`boards/x86/qemu/qemu-i486`)

## Overview
Board Support Package (BSP) blueprint for `qemu-i486` (`x86` / `qemu`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `ostest`, `vga_fb`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `qemu-i486` (`x86/qemu`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:PIT_CLOCK]` Hardware/board configuration macros (`PIT_CLOCK`).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `qemu-i486` (`x86/qemu`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[qemu_i486.h:qemu_bringup]` Public declaration `qemu_bringup()`.
