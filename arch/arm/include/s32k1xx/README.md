# s32k1xx (`nuttx/arch/arm/include/s32k1xx`)

## Overview
Hardware abstraction and architecture package for `s32k1xx` under `nuttx/arch/arm/include/s32k1xx`, providing 4 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`, `s32k11x_irq.h`, `s32k14x_irq.h`).

## Interface
- `[chip.h:NVIC_SYSH_PRIORITY_MIN]`
- `[chip.h:NVIC_SYSH_PRIORITY_DEFAULT]`
- `[chip.h:NVIC_SYSH_PRIORITY_MAX]`
- `[chip.h:NVIC_SYSH_PRIORITY_STEP]`
- `[s32k11x_irq.h:S32K1XX_IRQ_RESERVED]`
- `[s32k11x_irq.h:S32K1XX_IRQ_NMI]`
- `[s32k11x_irq.h:S32K1XX_IRQ_HARDFAULT]`
- `[s32k11x_irq.h:S32K1XX_IRQ_SVCALL]`
- `[s32k11x_irq.h:S32K1XX_IRQ_PENDSV]`
- `[s32k11x_irq.h:S32K1XX_IRQ_SYSTICK]`
- `[s32k11x_irq.h:S32K1XX_IRQ_INTERRUPT]`
- `[s32k11x_irq.h:S32K1XX_IRQ_DMACH0]`
- `[s32k11x_irq.h:S32K1XX_IRQ_DMACH1]`
- `[s32k11x_irq.h:S32K1XX_IRQ_DMACH2]`
- `[s32k11x_irq.h:S32K1XX_IRQ_DMACH3]`
- `[s32k11x_irq.h:S32K1XX_IRQ_DMACH_ERR]`
- `[s32k14x_irq.h:S32K1XX_IRQ_RESERVED]`
- `[s32k14x_irq.h:S32K1XX_IRQ_NMI]`
- `[s32k14x_irq.h:S32K1XX_IRQ_HARDFAULT]`
- `[s32k14x_irq.h:S32K1XX_IRQ_MEMFAULT]`
- `[s32k14x_irq.h:S32K1XX_IRQ_BUSFAULT]`
- `[s32k14x_irq.h:S32K1XX_IRQ_USAGEFAULT]`
- `[s32k14x_irq.h:S32K1XX_IRQ_SVCALL]`
- `[s32k14x_irq.h:S32K1XX_IRQ_DBGMONITOR]`
- `[s32k14x_irq.h:S32K1XX_IRQ_PENDSV]`
- `[s32k14x_irq.h:S32K1XX_IRQ_SYSTICK]`
- `[s32k14x_irq.h:S32K1XX_IRQ_INTERRUPT]`
- `[s32k14x_irq.h:S32K1XX_IRQ_DMACH0]`

## Invariants
- `[irq.h:#error]` Compile-time guard: Unrecognized S32K1XX part

## Side Effects
- None

## Verification
- Run: `make test`
