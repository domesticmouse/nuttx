# hardware (`nuttx/arch/arm64/src/bcm2711/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm64/src/bcm2711/hardware`, providing 15 header file(s) and 0 source file(s) (including `bcm2711_armtimer.h`, `bcm2711_aux.h`, `bcm2711_bsc.h`, `bcm2711_dma.h`).

## Interface
- `[bcm2711_armtimer.h:BCM_ARMT_LOAD_OFFSET]`
- `[bcm2711_armtimer.h:BCM_ARMT_VALUE_OFFSET]`
- `[bcm2711_armtimer.h:BCM_ARMT_CONTROL_OFFSET]`
- `[bcm2711_armtimer.h:BCM_ARMT_IRQCNTL_OFFSET]`
- `[bcm2711_armtimer.h:BCM_ARMT_RAWIRQ_OFFSET]`
- `[bcm2711_armtimer.h:BCM_ARMT_MSKIRQ_OFFSET]`
- `[bcm2711_armtimer.h:BCM_ARMT_RELOAD_OFFSET]`
- `[bcm2711_armtimer.h:BCM_ARMT_PREDIV_OFFSET]`
- `[bcm2711_armtimer.h:BCM_ARMT_FREECNT_OFFSET]`
- `[bcm2711_armtimer.h:_BCM_ARMT]`
- `[bcm2711_armtimer.h:BCM_ARMT_LOAD]`
- `[bcm2711_armtimer.h:BCM_ARMT_VALUE]`
- `[bcm2711_aux.h:BCM_AUX_IRQ_OFFSET]`
- `[bcm2711_aux.h:BCM_AUX_ENABLES_OFFSET]`
- `[bcm2711_aux.h:BCM_AUX_MU_IO_REG_OFFSET]`
- `[bcm2711_aux.h:BCM_AUX_MU_IER_REG_OFFSET]`
- `[bcm2711_aux.h:BCM_AUX_MU_IIR_REG_OFFSET]`
- `[bcm2711_aux.h:BCM_AUX_MU_LCR_REG_OFFSET]`
- `[bcm2711_aux.h:BCM_AUX_MU_MCR_REG_OFFSET]`
- `[bcm2711_aux.h:BCM_AUX_MU_LSR_REG_OFFSET]`
- `[bcm2711_aux.h:BCM_AUX_MU_MSR_REG_OFFSET]`
- `[bcm2711_aux.h:BCM_AUX_MU_SCRATCH_OFFSET]`
- `[bcm2711_aux.h:BCM_AUX_MU_CNTL_REG_OFFSET]`
- `[bcm2711_aux.h:BCM_AUX_MU_STAT_REG_OFFSET]`
- `[bcm2711_bsc.h:BCM_BSC0]`
- `[bcm2711_bsc.h:BCM_BSC1]`
- `[bcm2711_bsc.h:BCM_BSC3]`
- `[bcm2711_bsc.h:BCM_BSC4]`
- `[bcm2711_bsc.h:BCM_BSC5]`
- `[bcm2711_bsc.h:BCM_BSC6]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
