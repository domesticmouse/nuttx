# `imxrt1060-evk/include` Component (`boards/arm/imxrt/imxrt1060-evk/include`)

## Overview
Board-level public headers (`include`) for `imxrt1060-evk` (`arm/imxrt`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:IMXRT_VDD_SOC]` Hardware/board configuration macros (`IMXRT_VDD_SOC`, `BOARD_XTAL_FREQUENCY`, `IMXRT_PRE_PERIPH_CLK_SEL`, `IMXRT_PERIPH_CLK_SEL`, `IMXRT_ARM_PLL_DIV_SELECT`, `IMXRT_ARM_PODF_DIVIDER` (+98 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh imxrt1060-evk:nsh && make`
