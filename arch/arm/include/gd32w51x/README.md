# gd32w51x (`nuttx/arch/arm/include/gd32w51x`)

## Overview
Hardware abstraction and architecture package for `gd32w51x` under `nuttx/arch/arm/include/gd32w51x`, providing 2 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`).

## Interface
- `[chip.h:GD32W51X_FLASH_SIZE]`
- `[chip.h:GD32W51X_SRAM_SIZE]`
- `[chip.h:GD32W51X_QFN56]`
- `[chip.h:NVIC_SYSH_PRIORITY_MIN]`
- `[chip.h:NVIC_SYSH_PRIORITY_DEFAULT]`
- `[chip.h:NVIC_SYSH_PRIORITY_MAX]`
- `[chip.h:NVIC_SYSH_PRIORITY_STEP]`
- `[irq.h:GD32W51X_IRQ_RESERVED]`
- `[irq.h:GD32W51X_IRQ_NMI]`
- `[irq.h:GD32W51X_IRQ_HARDFAULT]`
- `[irq.h:GD32W51X_IRQ_MEMFAULT]`
- `[irq.h:GD32W51X_IRQ_BUSFAULT]`
- `[irq.h:GD32W51X_IRQ_USAGEFAULT]`
- `[irq.h:GD32W51X_IRQ_SECUREFAULT]`
- `[irq.h:GD32W51X_IRQ_SVCALL]`
- `[irq.h:GD32W51X_IRQ_DBGMONITOR]`
- `[irq.h:GD32W51X_IRQ_PENDSV]`
- `[irq.h:GD32W51X_IRQ_SYSTICK]`
- `[irq.h:GD32W51X_IRQ_EXTINT]`

## Invariants
- `[chip.h:#error]` Compile-time guard: Unknown GD32W51x chip variant

## Side Effects
- None

## Verification
- Run: `make test`
