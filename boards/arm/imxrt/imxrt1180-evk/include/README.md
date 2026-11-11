# `imxrt1180-evk/include` Component (`boards/arm/imxrt/imxrt1180-evk/include`)

## Overview
Board-level public headers (`include`) for `imxrt1180-evk` (`arm/imxrt`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s).

## Interface
- `[board.h:GPIO_FLEXSPI_DQS]` Hardware/board configuration macros (`GPIO_FLEXSPI_DQS`, `GPIO_FLEXSPI_SCK`, `GPIO_FLEXSPI_CS`, `GPIO_FLEXSPI_IO0`, `GPIO_FLEXSPI_IO1`, `GPIO_FLEXSPI_IO2` (+49 more))
- `[imxrt118x_trdc_config.h:RWX]` Hardware/board configuration macros (`RWX`, `TRDC_FULL_ACCESS_GLBAC`, `DID_CM33`, `DID_EDMA3_RESET`, `DID_CM7`, `DID_USDHC1` (+27 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh imxrt1180-evk:nsh && make`
