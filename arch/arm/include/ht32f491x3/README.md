# ht32f491x3 (`nuttx/arch/arm/include/ht32f491x3`)

## Overview
Hardware abstraction and architecture package for `ht32f491x3` under `nuttx/arch/arm/include/ht32f491x3`, providing 3 header file(s) and 0 source file(s) (including `chip.h`, `ht32f491x3_irq.h`, `irq.h`).

## Interface
- `[chip.h:HT32M4_SYSH_PRIORITY_MIN]`
- `[chip.h:HT32M4_SYSH_PRIORITY_DEFAULT]`
- `[chip.h:HT32M4_SYSH_PRIORITY_MAX]`
- `[chip.h:HT32M4_SYSH_PRIORITY_STEP]`
- `[chip.h:NVIC_SYSH_PRIORITY_MIN]`
- `[chip.h:NVIC_SYSH_PRIORITY_DEFAULT]`
- `[chip.h:NVIC_SYSH_PRIORITY_MAX]`
- `[chip.h:NVIC_SYSH_PRIORITY_STEP]`
- `[chip.h:HT32_FLASH_KB]`
- `[chip.h:HT32_SRAM_KB]`
- `[chip.h:HT32_NUSART]`
- `[ht32f491x3_irq.h:HT32_IRQ_WWDT]`
- `[ht32f491x3_irq.h:HT32_IRQ_PVM]`
- `[ht32f491x3_irq.h:HT32_IRQ_PVD]`
- `[ht32f491x3_irq.h:HT32_IRQ_TAMP_STAMP]`
- `[ht32f491x3_irq.h:HT32_IRQ_TAMPER]`
- `[ht32f491x3_irq.h:HT32_IRQ_TIMESTAMP]`
- `[ht32f491x3_irq.h:HT32_IRQ_ERTCWAKEUP]`
- `[ht32f491x3_irq.h:HT32_IRQ_FLASH]`
- `[ht32f491x3_irq.h:HT32_IRQ_CRM]`
- `[ht32f491x3_irq.h:HT32_IRQ_EXINT0]`
- `[ht32f491x3_irq.h:HT32_IRQ_EXINT1]`
- `[ht32f491x3_irq.h:HT32_IRQ_EXINT2]`
- `[irq.h:HT32_IRQ_RESERVED]`
- `[irq.h:HT32_IRQ_NMI]`
- `[irq.h:HT32_IRQ_HARDFAULT]`
- `[irq.h:HT32_IRQ_MEMFAULT]`
- `[irq.h:HT32_IRQ_BUSFAULT]`
- `[irq.h:HT32_IRQ_USAGEFAULT]`
- `[irq.h:HT32_IRQ_SVCALL]`

## Invariants
- `[chip.h:#error]` Compile-time guard: Unsupported HT32F491x3 device

## Side Effects
- None

## Verification
- Run: `make test`
