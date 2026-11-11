# mcx-nxxx (`nuttx/arch/arm/include/mcx-nxxx`)

## Overview
Hardware abstraction and architecture package for `mcx-nxxx` under `nuttx/arch/arm/include/mcx-nxxx`, providing 3 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`, `n236_irq.h`).

## Interface
- `[chip.h:ARMV8M_ICACHE_LINESIZE]`
- `[chip.h:ARMV8M_DCACHE_LINESIZE]`
- `[chip.h:NVIC_SYSH_PRIORITY_MIN]`
- `[chip.h:NVIC_SYSH_PRIORITY_DEFAULT]`
- `[chip.h:NVIC_SYSH_PRIORITY_MAX]`
- `[chip.h:NVIC_SYSH_PRIORITY_STEP]`
- `[chip.h:NXXX_GPIO_NPORTS]`
- `[irq.h:NXXX_IRQ_RESERVED]`
- `[irq.h:NXXX_IRQ_NMI]`
- `[irq.h:NXXX_IRQ_HARDFAULT]`
- `[irq.h:NXXX_IRQ_MEMFAULT]`
- `[irq.h:NXXX_IRQ_BUSFAULT]`
- `[irq.h:NXXX_IRQ_USAGEFAULT]`
- `[irq.h:NXXX_IRQ_SVCALL]`
- `[irq.h:NXXX_IRQ_DBGMONITOR]`
- `[irq.h:NXXX_IRQ_PENDSV]`
- `[irq.h:NXXX_IRQ_SYSTICK]`
- `[irq.h:NXXX_IRQ_EXTINT]`
- `[n236_irq.h:ARCH_ARM_INCLUDE_MCX_NXXX_N236_IRQ_H]`
- `[n236_irq.h:NXXX_IRQ_OR]`
- `[n236_irq.h:NXXX_IRQ_EDMA_0_CH0]`
- `[n236_irq.h:NXXX_IRQ_EDMA_0_CH1]`
- `[n236_irq.h:NXXX_IRQ_EDMA_0_CH2]`
- `[n236_irq.h:NXXX_IRQ_EDMA_0_CH3]`
- `[n236_irq.h:NXXX_IRQ_EDMA_0_CH4]`
- `[n236_irq.h:NXXX_IRQ_EDMA_0_CH5]`
- `[n236_irq.h:NXXX_IRQ_EDMA_0_CH6]`
- `[n236_irq.h:NXXX_IRQ_EDMA_0_CH7]`
- `[n236_irq.h:NXXX_IRQ_EDMA_0_CH8]`
- `[n236_irq.h:NXXX_IRQ_EDMA_0_CH9]`

## Invariants
- `[irq.h:#error]` Compile-time guard: Unrecognized MCX-NXXx architecture

## Side Effects
- None

## Verification
- Run: `make test`
