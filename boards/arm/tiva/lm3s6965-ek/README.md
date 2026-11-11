# `lm3s6965-ek` Board Support Package (`boards/arm/tiva/lm3s6965-ek`)

## Overview
Board Support Package (BSP) blueprint for `lm3s6965-ek` (`arm` / `tiva`). Coordinates board initialization, headers, and tooling across `include, kernel, src, tools`. Includes build configurations: `discover`, `nsh`, `nx`, `qemu-flat`, `qemu-kostest`, `qemu-nxflat` (+2 more).

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `lm3s6965-ek` (`arm/tiva`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:SYSCON_RCC_XTAL]` Hardware/board configuration macros (`SYSCON_RCC_XTAL`, `XTAL_FREQUENCY`, `SYSCON_RCC_OSCSRC`, `SYSCON_RCC2_OSCSRC`, `OSCSRC_FREQUENCY`, `TIVA_SYSDIV` (+12 more)).
- [`kernel`](./kernel/README.md) - Protected-build userspace/kernel boundary module (`kernel`) for `lm3s6965-ek` (`arm/tiva`), providing userspace initialization and syscall/gate hooks across 1 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `lm3s6965-ek` (`arm/tiva`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
- [`tools`](./tools/README.md) - Board support component `tools` for `lm3s6965-ek` (`arm/tiva`), containing 1 source/script file(s) (`oocd.sh`). Key symbols: `[oocd.sh]` Shell script entry point `oocd.sh`.
