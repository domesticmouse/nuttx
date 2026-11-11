# `lm3s8962-ek` Board Support Package (`boards/arm/tiva/lm3s8962-ek`)

## Overview
Board Support Package (BSP) blueprint for `lm3s8962-ek` (`arm` / `tiva`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `nx`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `lm3s8962-ek` (`arm/tiva`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:SYSCON_RCC_XTAL]` Hardware/board configuration macros (`SYSCON_RCC_XTAL`, `XTAL_FREQUENCY`, `SYSCON_RCC_OSCSRC`, `SYSCON_RCC2_OSCSRC`, `OSCSRC_FREQUENCY`, `TIVA_SYSDIV` (+12 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `lm3s8962-ek` (`arm/tiva`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 6 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
