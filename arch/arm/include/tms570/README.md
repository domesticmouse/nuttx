# tms570 (`nuttx/arch/arm/include/tms570`)

## Overview
Hardware abstraction and architecture package for `tms570` under `nuttx/arch/arm/include/tms570`, providing 3 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`, `tms570ls04x03x_irq.h`).

## Interface
- `[chip.h:TMS570_CORTEX_R4]`
- `[chip.h:TMS570_PFLASH]`
- `[chip.h:TMS570_SRAM]`
- `[chip.h:TMS570_DFLASH]`
- `[chip.h:TMS570_NEMAC]`
- `[chip.h:TMS570_FLEXRAY_NCH]`
- `[chip.h:TMS570_NCAN]`
- `[chip.h:TMS570_NMIBADC]`
- `[chip.h:TMS570_MIBADC_NCH]`
- `[chip.h:TMS570_NN2HET]`
- `[chip.h:TMS570_N2HET_NCH]`
- `[chip.h:TMS570_EPWM_NCH]`
- `[irq.h:TMS570_VECT_PHANTOM]`
- `[irq.h:NR_IRQS]`
- `[tms570ls04x03x_irq.h:TMS570_IRQ_NCHANNELS]`
- `[tms570ls04x03x_irq.h:TMS570_REQ_ESMHIGH]`
- `[tms570ls04x03x_irq.h:TMS570_REQ_RTICMP0]`
- `[tms570ls04x03x_irq.h:TMS570_REQ_RTICMP1]`
- `[tms570ls04x03x_irq.h:TMS570_REQ_RTICMP2]`
- `[tms570ls04x03x_irq.h:TMS570_REQ_RTICMP3]`
- `[tms570ls04x03x_irq.h:TMS570_REQ_RTIOVF0]`
- `[tms570ls04x03x_irq.h:TMS570_REQ_RTIOVF1]`
- `[tms570ls04x03x_irq.h:TMS570_REQ_GIO_0]`
- `[tms570ls04x03x_irq.h:TMS570_REQ_N2HET_0]`
- `[tms570ls04x03x_irq.h:TMS570_REQ_HTU_0]`
- `[tms570ls04x03x_irq.h:TMS570_REQ_MIBSPI1_0]`

## Invariants
- `[chip.h:#error]` Compile-time guard: Unrecognized TMS570 chip
- `[irq.h:#error]` Compile-time guard: No IRQ definitions for the TMS570LS0232PZ

## Side Effects
- None

## Verification
- Run: `make test`
