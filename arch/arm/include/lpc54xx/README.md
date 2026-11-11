# lpc54xx (`nuttx/arch/arm/include/lpc54xx`)

## Overview
Hardware abstraction and architecture package for `lpc54xx` under `nuttx/arch/arm/include/lpc54xx`, providing 3 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`, `lpc546x_irq.h`).

## Interface
- `[chip.h:NVIC_SYSH_PRIORITY_MIN]`
- `[chip.h:NVIC_SYSH_PRIORITY_DEFAULT]`
- `[chip.h:NVIC_SYSH_PRIORITY_MAX]`
- `[chip.h:NVIC_SYSH_PRIORITY_STEP]`
- `[irq.h:LPC54_IRQ_RESERVED]`
- `[irq.h:LPC54_IRQ_NMI]`
- `[irq.h:LPC54_IRQ_HARDFAULT]`
- `[irq.h:LPC54_IRQ_MEMFAULT]`
- `[irq.h:LPC54_IRQ_BUSFAULT]`
- `[irq.h:LPC54_IRQ_USAGEFAULT]`
- `[irq.h:LPC54_IRQ_SIGNVALUE]`
- `[irq.h:LPC54_IRQ_SVCALL]`
- `[irq.h:LPC54_IRQ_DBGMONITOR]`
- `[irq.h:LPC54_IRQ_PENDSV]`
- `[irq.h:LPC54_IRQ_SYSTICK]`
- `[irq.h:LPC54_IRQ_EXTINT]`
- `[lpc546x_irq.h:LPC54_IRQ_WDT]`
- `[lpc546x_irq.h:LPC54_IRQ_DMA]`
- `[lpc546x_irq.h:LPC54_IRQ_GINT0]`
- `[lpc546x_irq.h:LPC54_IRQ_GINT1]`
- `[lpc546x_irq.h:LPC54_IRQ_PININT0]`
- `[lpc546x_irq.h:LPC54_IRQ_PININT1]`
- `[lpc546x_irq.h:LPC54_IRQ_PININT2]`
- `[lpc546x_irq.h:LPC54_IRQ_PININT3]`
- `[lpc546x_irq.h:LPC54_IRQ_UTICK]`
- `[lpc546x_irq.h:LPC54_IRQ_MRT]`
- `[lpc546x_irq.h:LPC54_IRQ_CTIMER0]`
- `[lpc546x_irq.h:LPC54_IRQ_CTIMER1]`

## Invariants
- `[irq.h:#error]` Compile-time guard: Unsupported LPC54 MCU

## Side Effects
- None

## Verification
- Run: `make test`
