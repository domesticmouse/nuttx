# imx95 (`nuttx/arch/arm/src/imx9/hardware/imx95`)

## Overview
Hardware abstraction and architecture package for `imx95` under `nuttx/arch/arm/src/imx9/hardware/imx95`, providing 7 header file(s) and 0 source file(s) (including `imx95_clock.h`, `imx95_dmamux.h`, `imx95_edma.h`, `imx95_gpio.h`).

## Interface
- `[imx95_clock.h:clock_id_e]`
- `[imx95_clock.h:clock_config_t]`
- `[imx95_clock.h:XTAL_FREQ]`
- `[imx95_clock.h:ROOT_CLOCK_OFFSET]`
- `[imx95_clock.h:CCM_CR_COUNT]`
- `[imx95_clock.h:CLOCK_DIV_SHIFT]`
- `[imx95_clock.h:CLOCK_DIV_MASK]`
- `[imx95_clock.h:CLOCK_DIV]`
- `[imx95_clock.h:GET_CLOCK_DIV]`
- `[imx95_clock.h:CLOCK_ROOT_SHIFT]`
- `[imx95_clock.h:CLOCK_ROOT_MASK]`
- `[imx95_clock.h:CLOCK_ROOT]`
- `[imx95_clock.h:GET_CLOCK_ROOT]`
- `[imx95_clock.h:CLOCK_ID_SHIFT]`
- `[imx95_dmamux.h:EDMA3_MUX_ID]`
- `[imx95_dmamux.h:EDMA4_MUX_ID]`
- `[imx95_dmamux.h:EDMA_MUX_ID_MASK]`
- `[imx95_dmamux.h:EDMA_MUX_MASK]`
- `[imx95_dmamux.h:DMA_REQUEST_DISABLED]`
- `[imx95_dmamux.h:DMA_REQUEST_MUXCAN1]`
- `[imx95_dmamux.h:DMA_REQUEST_MUXLPTMR1REQUEST]`
- `[imx95_dmamux.h:DMA_REQUEST_MUXELEREQUEST]`
- `[imx95_dmamux.h:DMA_REQUEST_MUXTPM1OVERFLOWREQUEST]`
- `[imx95_dmamux.h:DMA_REQUEST_MUXTPM2OVERFLOWREQUEST]`
- `[imx95_dmamux.h:DMA_REQUEST_MUXPDMREQUEST]`
- `[imx95_dmamux.h:DMA_REQUEST_MUXADC1REQUEST]`
- `[imx95_edma.h:imx9_edmatcd_s]`
- `[imx95_edma.h:IMX9_EDMA_CSR_OFFSET]`
- `[imx95_edma.h:IMX9_EDMA_ES_OFFSET]`
- `[imx95_edma.h:IMX9_EDMA_CH_GRPRI_OFFSET]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
