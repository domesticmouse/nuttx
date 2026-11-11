# xmc4 (`nuttx/arch/arm/include/xmc4`)

## Overview
Hardware abstraction and architecture package for `xmc4` under `nuttx/arch/arm/include/xmc4`, providing 5 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`, `xmc4500_irq.h`, `xmc4700_irq.h`).

## Interface
- `[chip.h:XMC4_NUSIC]`
- `[chip.h:XMC4_NECAT]`
- `[chip.h:XMC4_SCU_GATING]`
- `[chip.h:NVIC_SYSH_PRIORITY_MIN]`
- `[chip.h:NVIC_SYSH_PRIORITY_DEFAULT]`
- `[chip.h:NVIC_SYSH_PRIORITY_MAX]`
- `[chip.h:NVIC_SYSH_PRIORITY_STEP]`
- `[irq.h:XMC4_IRQ_RESERVED]`
- `[irq.h:XMC4_IRQ_NMI]`
- `[irq.h:XMC4_IRQ_HARDFAULT]`
- `[irq.h:XMC4_IRQ_MEMFAULT]`
- `[irq.h:XMC4_IRQ_BUSFAULT]`
- `[irq.h:XMC4_IRQ_USAGEFAULT]`
- `[irq.h:XMC4_IRQ_SVCALL]`
- `[irq.h:XMC4_IRQ_DBGMONITOR]`
- `[irq.h:XMC4_IRQ_PENDSV]`
- `[irq.h:XMC4_IRQ_SYSTICK]`
- `[irq.h:XMC4_IRQ_FIRST]`
- `[xmc4500_irq.h:xmc4__ARCH_ARM_INCLUDE_XMC4_XM4500_IRQ_H]`
- `[xmc4500_irq.h:XMC4_IRQ_SCU]`
- `[xmc4500_irq.h:XMC4_IRQ_ERU0_SR0]`
- `[xmc4500_irq.h:XMC4_IRQ_ERU0_SR1]`
- `[xmc4500_irq.h:XMC4_IRQ_ERU0_SR2]`
- `[xmc4500_irq.h:XMC4_IRQ_ERU0_SR3]`
- `[xmc4500_irq.h:XMC4_IRQ_ERU1_SR0]`
- `[xmc4500_irq.h:XMC4_IRQ_ERU1_SR1]`
- `[xmc4500_irq.h:XMC4_IRQ_ERU1_SR2]`
- `[xmc4500_irq.h:XMC4_IRQ_ERU1_SR3]`
- `[xmc4500_irq.h:XMC4_IRQ_RESVD009]`
- `[xmc4500_irq.h:XMC4_IRQ_RESVD010]`

## Invariants
- `[chip.h:#error]` Compile-time guard: Unsupported XMC4xxx chip
- `[irq.h:#error]` Compile-time guard: No IRQ numbers for this XMC4xxx part

## Side Effects
- None

## Verification
- Run: `make test`
