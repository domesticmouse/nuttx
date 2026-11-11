# s32k3xx (`nuttx/arch/arm/include/s32k3xx`)

## Overview
Hardware abstraction and architecture package for `s32k3xx` under `nuttx/arch/arm/include/s32k3xx`, providing 3 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`, `s32k3x4_irq.h`).

## Interface
- `[chip.h:NVIC_SYSH_PRIORITY_MIN]`
- `[chip.h:NVIC_SYSH_PRIORITY_DEFAULT]`
- `[chip.h:NVIC_SYSH_PRIORITY_MAX]`
- `[chip.h:NVIC_SYSH_PRIORITY_STEP]`
- `[irq.h:S32K3XX_IRQ_RESERVED]`
- `[irq.h:S32K3XX_IRQ_NMI]`
- `[irq.h:S32K3XX_IRQ_HARDFAULT]`
- `[irq.h:S32K3XX_IRQ_MEMFAULT]`
- `[irq.h:S32K3XX_IRQ_BUSFAULT]`
- `[irq.h:S32K3XX_IRQ_USAGEFAULT]`
- `[irq.h:S32K3XX_IRQ_SVCALL]`
- `[irq.h:S32K3XX_IRQ_DBGMONITOR]`
- `[irq.h:S32K3XX_IRQ_PENDSV]`
- `[irq.h:S32K3XX_IRQ_SYSTICK]`
- `[irq.h:S32K3XX_IRQ_EXTINT]`
- `[s32k3x4_irq.h:S32K3XX_IRQ_CPU_TO_CPU1]`
- `[s32k3x4_irq.h:S32K3XX_IRQ_CPU_TO_CPU2]`
- `[s32k3x4_irq.h:S32K3XX_IRQ_CPU_TO_CPU3]`
- `[s32k3x4_irq.h:S32K3XX_IRQ_CPU_TO_CPU4]`
- `[s32k3x4_irq.h:S32K3XX_IRQ_DMA_CH0]`
- `[s32k3x4_irq.h:S32K3XX_IRQ_DMA_CH1]`
- `[s32k3x4_irq.h:S32K3XX_IRQ_DMA_CH2]`
- `[s32k3x4_irq.h:S32K3XX_IRQ_DMA_CH3]`
- `[s32k3x4_irq.h:S32K3XX_IRQ_DMA_CH4]`
- `[s32k3x4_irq.h:S32K3XX_IRQ_DMA_CH5]`
- `[s32k3x4_irq.h:S32K3XX_IRQ_DMA_CH6]`
- `[s32k3x4_irq.h:S32K3XX_IRQ_DMA_CH7]`

## Invariants
- `[irq.h:#error]` Compile-time guard: Unrecognized S32K3XX part

## Side Effects
- None

## Verification
- Run: `make test`
