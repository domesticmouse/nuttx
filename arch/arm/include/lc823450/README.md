# lc823450 (`nuttx/arch/arm/include/lc823450`)

## Overview
Hardware abstraction and architecture package for `lc823450` under `nuttx/arch/arm/include/lc823450`, providing 3 header file(s) and 0 source file(s) (including `chip.h`, `clk.h`, `irq.h`).

## Interface
- `[chip.h:NVIC_SYSH_PRIORITY_MIN]`
- `[chip.h:NVIC_SYSH_PRIORITY_DEFAULT]`
- `[chip.h:NVIC_SYSH_PRIORITY_MAX]`
- `[chip.h:NVIC_SYSH_PRIORITY_STEP]`
- `[clk.h:up_enable_clk]`
- `[clk.h:up_disable_clk]`
- `[clk.h:clk_st]`
- `[clk.h:clock_e]`
- `[clk.h:LC823450_CLOCKS]`
- `[irq.h:lc823450_irq_srctype]`
- `[irq.h:lc823450_irq_register]`
- `[irq.h:lc823450_srctype_e]`
- `[irq.h:lc823450_irq_ops]`
- `[irq.h:LC823450_IRQ_RESERVED]`
- `[irq.h:LC823450_IRQ_NMI]`
- `[irq.h:LC823450_IRQ_HARDFAULT]`
- `[irq.h:LC823450_IRQ_MEMFAULT]`
- `[irq.h:LC823450_IRQ_BUSFAULT]`
- `[irq.h:LC823450_IRQ_USAGEFAULT]`
- `[irq.h:LC823450_IRQ_SVCALL]`
- `[irq.h:LC823450_IRQ_DBGMONITOR]`
- `[irq.h:LC823450_IRQ_PENDSV]`
- `[irq.h:LC823450_IRQ_SYSTICK]`
- `[irq.h:LC823450_IRQ_INTERRUPTS]`
- `[irq.h:LC823450_IRQ_CTXM3_00]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
