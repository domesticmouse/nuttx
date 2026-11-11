# `ddcnc-ec300` Board Support Package (`boards/arm/imxrt/ddcnc-ec300`)

## Overview
Board Support Package (BSP) blueprint for `ddcnc-ec300` (`arm` / `imxrt`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `netnsh`, `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `ddcnc-ec300` (`arm/imxrt`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:IMXRT_VDD_SOC]` Hardware/board configuration macros (`IMXRT_VDD_SOC`, `BOARD_XTAL_FREQUENCY`, `IMXRT_PRE_PERIPH_CLK_SEL`, `IMXRT_PERIPH_CLK_SEL`, `IMXRT_ARM_PLL_DIV_SELECT`, `IMXRT_ARM_PODF_DIVIDER` (+40 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `ddcnc-ec300` (`arm/imxrt`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 10 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
