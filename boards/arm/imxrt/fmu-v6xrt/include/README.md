# `fmu-v6xrt/include` Component (`boards/arm/imxrt/fmu-v6xrt/include`)

## Overview
Board-level public headers (`include`) for `fmu-v6xrt` (`arm/imxrt`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_CPU_FREQUENCY]` Hardware/board configuration macros (`BOARD_CPU_FREQUENCY`, `IMXRT_IPG_PODF_DIVIDER`, `BOARD_GPT_FREQUENCY`, `BOARD_XTAL_FREQUENCY`, `BOARD_FLEXIO_PREQ`, `PIN_USDHC1_D0` (+121 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh fmu-v6xrt:nsh && make`
