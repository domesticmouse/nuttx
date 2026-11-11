# samv7 (`nuttx/arch/arm/include/samv7`)

## Overview
Hardware abstraction and architecture package for `samv7` under `nuttx/arch/arm/include/samv7`, providing 5 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`, `sam_afec.h`, `same70_irq.h`).

## Interface
- `[chip.h:SAMV7_FLASH_SIZE]`
- `[chip.h:SAMV7_SRAM_SIZE]`
- `[chip.h:SAMV7_BSRAM_SIZE]`
- `[chip.h:SAMV7_NPIO]`
- `[chip.h:SAMV7_NEBI]`
- `[chip.h:SAMV7_NSDRAMC]`
- `[chip.h:SAMV7_NMLB]`
- `[chip.h:SAMV7_NDMACHAN]`
- `[irq.h:SAM_IRQ_RESERVED]`
- `[irq.h:SAM_IRQ_NMI]`
- `[irq.h:SAM_IRQ_HARDFAULT]`
- `[irq.h:SAM_IRQ_MEMFAULT]`
- `[irq.h:SAM_IRQ_BUSFAULT]`
- `[irq.h:SAM_IRQ_USAGEFAULT]`
- `[irq.h:SAM_IRQ_SVCALL]`
- `[irq.h:SAM_IRQ_DBGMONITOR]`
- `[irq.h:SAM_IRQ_PENDSV]`
- `[irq.h:SAM_IRQ_SYSTICK]`
- `[irq.h:SAM_IRQ_EXTINT]`
- `[sam_afec.h:sam_afec_gain_param_tds]`
- `[sam_afec.h:ANIOC_SAMV7_AFEC_IOCTRL_GAIN]`
- `[same70_irq.h:SAM_PID_SUPC]`
- `[same70_irq.h:SAM_PID_RSTC]`
- `[same70_irq.h:SAM_PID_RTC]`
- `[same70_irq.h:SAM_PID_RTT]`
- `[same70_irq.h:SAM_PID_WDT]`
- `[same70_irq.h:SAM_PID_PMC]`
- `[same70_irq.h:SAM_PID_EFC]`
- `[same70_irq.h:SAM_PID_UART0]`
- `[same70_irq.h:SAM_PID_UART1]`

## Invariants
- `[chip.h:#error]` Compile-time guard: Unknown package of PIC32CZCA70 chip
- `[irq.h:#error]` Compile-time guard: Unrecognized SAMV7 architecture

## Side Effects
- None

## Verification
- Run: `make test`
