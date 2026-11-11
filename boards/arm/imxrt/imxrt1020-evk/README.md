# `imxrt1020-evk` Board Support Package (`boards/arm/imxrt/imxrt1020-evk`)

## Overview
Board Support Package (BSP) blueprint for `imxrt1020-evk` (`arm` / `imxrt`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `netnsh`, `nsh`, `usdhc`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `imxrt1020-evk` (`arm/imxrt`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:IMXRT_VDD_SOC]` Hardware/board configuration macros (`IMXRT_VDD_SOC`, `BOARD_XTAL_FREQUENCY`, `BOARD_CPU_FREQUENCY`, `IMXRT_PRE_PERIPH_CLK_SEL`, `IMXRT_PERIPH_CLK_SEL`, `IMXRT_ARM_PODF_DIVIDER` (+69 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `imxrt1020-evk` (`arm/imxrt`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 14 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
