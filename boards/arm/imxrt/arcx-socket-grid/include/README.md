# `arcx-socket-grid/include` Component (`boards/arm/imxrt/arcx-socket-grid/include`)

## Overview
Board-level public headers (`include`) for `arcx-socket-grid` (`arm/imxrt`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:IMXRT_VDD_SOC]` Hardware/board configuration macros (`IMXRT_VDD_SOC`, `BOARD_XTAL_FREQUENCY`, `IMXRT_PRE_PERIPH_CLK_SEL`, `IMXRT_PERIPH_CLK_SEL`, `IMXRT_ARM_PLL_DIV_SELECT`, `IMXRT_ARM_PODF_DIVIDER` (+106 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh arcx-socket-grid:nsh && make`
