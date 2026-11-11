# imxrt (`nuttx/arch/arm/include/imxrt`)

## Overview
Hardware abstraction and architecture package for `imxrt` under `nuttx/arch/arm/include/imxrt`, providing 8 header file(s) and 0 source file(s) (including `chip.h`, `imxrt102x_irq.h`, `imxrt105x_irq.h`, `imxrt106x_irq.h`).

## Interface
- `[chip.h:IMXRT_OCRAM_SIZE]`
- `[chip.h:IMXRT_GPIO_NPORTS]`
- `[chip.h:NVIC_SYSH_PRIORITY_MIN]`
- `[chip.h:NVIC_SYSH_PRIORITY_DEFAULT]`
- `[chip.h:NVIC_SYSH_PRIORITY_MAX]`
- `[chip.h:NVIC_SYSH_PRIORITY_STEP]`
- `[imxrt102x_irq.h:IMXRT_IRQ_EDMA0_16]`
- `[imxrt102x_irq.h:IMXRT_IRQ_EDMA1_17]`
- `[imxrt102x_irq.h:IMXRT_IRQ_EDMA2_18]`
- `[imxrt102x_irq.h:IMXRT_IRQ_EDMA3_19]`
- `[imxrt102x_irq.h:IMXRT_IRQ_EDMA4_20]`
- `[imxrt102x_irq.h:IMXRT_IRQ_EDMA5_21]`
- `[imxrt102x_irq.h:IMXRT_IRQ_EDMA6_22]`
- `[imxrt102x_irq.h:IMXRT_IRQ_EDMA7_23]`
- `[imxrt102x_irq.h:IMXRT_IRQ_EDMA8_24]`
- `[imxrt102x_irq.h:IMXRT_IRQ_EDMA9_25]`
- `[imxrt102x_irq.h:IMXRT_IRQ_EDMA10_26]`
- `[imxrt102x_irq.h:IMXRT_IRQ_EDMA11_27]`
- `[imxrt105x_irq.h:IMXRT_IRQ_EDMA0_16]`
- `[imxrt105x_irq.h:IMXRT_IRQ_EDMA1_17]`
- `[imxrt105x_irq.h:IMXRT_IRQ_EDMA2_18]`
- `[imxrt105x_irq.h:IMXRT_IRQ_EDMA3_19]`
- `[imxrt105x_irq.h:IMXRT_IRQ_EDMA4_20]`
- `[imxrt105x_irq.h:IMXRT_IRQ_EDMA5_21]`
- `[imxrt105x_irq.h:IMXRT_IRQ_EDMA6_22]`
- `[imxrt105x_irq.h:IMXRT_IRQ_EDMA7_23]`
- `[imxrt105x_irq.h:IMXRT_IRQ_EDMA8_24]`
- `[imxrt105x_irq.h:IMXRT_IRQ_EDMA9_25]`
- `[imxrt105x_irq.h:IMXRT_IRQ_EDMA10_26]`
- `[imxrt105x_irq.h:IMXRT_IRQ_EDMA11_27]`

## Invariants
- `[chip.h:#error]` Compile-time guard: Unknown i.MX RT chip type
- `[irq.h:#error]` Compile-time guard: Unrecognized i.MX RT architecture

## Side Effects
- None

## Verification
- Run: `make test`
