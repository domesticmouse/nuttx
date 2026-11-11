# lpc17xx_40xx (`nuttx/arch/arm/include/lpc17xx_40xx`)

## Overview
Hardware abstraction and architecture package for `lpc17xx_40xx` under `nuttx/arch/arm/include/lpc17xx_40xx`, providing 4 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`, `lpc176x_irq.h`, `lpc178x_40xx_irq.h`).

## Interface
- `[chip.h:LPC176x]`
- `[chip.h:LPC17_40_FLASH_SIZE]`
- `[chip.h:LPC17_40_SRAM_SIZE]`
- `[chip.h:LPC17_40_CPUSRAM_SIZE]`
- `[chip.h:LPC17_40_NETHCONTROLLERS]`
- `[chip.h:LPC17_40_NUSBHOST]`
- `[chip.h:LPC17_40_NUSBOTG]`
- `[chip.h:LPC17_40_NUSBDEV]`
- `[chip.h:LPC17_40_NCAN]`
- `[chip.h:LPC17_40_NI2S]`
- `[chip.h:LPC17_40_NDAC]`
- `[irq.h:LPC17_40_IRQ_RESERVED]`
- `[irq.h:LPC17_40_IRQ_NMI]`
- `[irq.h:LPC17_40_IRQ_HARDFAULT]`
- `[irq.h:LPC17_40_IRQ_MEMFAULT]`
- `[irq.h:LPC17_40_IRQ_BUSFAULT]`
- `[irq.h:LPC17_40_IRQ_USAGEFAULT]`
- `[irq.h:LPC17_40_IRQ_SVCALL]`
- `[irq.h:LPC17_40_IRQ_DBGMONITOR]`
- `[irq.h:LPC17_40_IRQ_PENDSV]`
- `[irq.h:LPC17_40_IRQ_SYSTICK]`
- `[irq.h:LPC17_40_IRQ_EXTINT]`
- `[lpc176x_irq.h:LPC17_40_IRQ_WDT]`
- `[lpc176x_irq.h:LPC17_40_IRQ_TMR0]`
- `[lpc176x_irq.h:LPC17_40_IRQ_TMR1]`
- `[lpc176x_irq.h:LPC17_40_IRQ_TMR2]`
- `[lpc176x_irq.h:LPC17_40_IRQ_TMR3]`
- `[lpc176x_irq.h:LPC17_40_IRQ_UART0]`
- `[lpc176x_irq.h:LPC17_40_IRQ_UART1]`
- `[lpc176x_irq.h:LPC17_40_IRQ_UART2]`

## Invariants
- `[chip.h:#error]` Compile-time guard: Unsupported LPC17xx/LPC40xx chip
- `[irq.h:#error]` Compile-time guard: Unknown LPC17xx/LPC40xx family

## Side Effects
- None

## Verification
- Run: `make test`
