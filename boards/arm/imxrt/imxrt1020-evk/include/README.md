# `imxrt1020-evk/include` Component (`boards/arm/imxrt/imxrt1020-evk/include`)

## Overview
Board-level public headers (`include`) for `imxrt1020-evk` (`arm/imxrt`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:IMXRT_VDD_SOC]` Hardware/board configuration macros (`IMXRT_VDD_SOC`, `BOARD_XTAL_FREQUENCY`, `BOARD_CPU_FREQUENCY`, `IMXRT_PRE_PERIPH_CLK_SEL`, `IMXRT_PERIPH_CLK_SEL`, `IMXRT_ARM_PODF_DIVIDER` (+69 more))

## Invariants
- `[board.h:#error]` Compile-time guard: `GPIO_ENET_IRQ Host IRQ not defined!`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh imxrt1020-evk:nsh && make`
