# stm32n6 (`nuttx/arch/arm/include/stm32n6`)

## Overview
Hardware abstraction and architecture package for `stm32n6` under `nuttx/arch/arm/include/stm32n6`, providing 3 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`, `stm32n6xx_irq.h`).

## Interface
- `[chip.h:STM32_SRAM_SIZE]`
- `[chip.h:STM32_NPORTS]`
- `[chip.h:STM32_NLPUART]`
- `[chip.h:STM32_NUSART]`
- `[chip.h:STM32_NUART]`
- `[chip.h:STM32_NATIM]`
- `[chip.h:STM32_NBTIM]`
- `[chip.h:STM32_NI2C]`
- `[chip.h:STM32_NSPI]`
- `[chip.h:NVIC_SYSH_PRIORITY_MIN]`
- `[chip.h:NVIC_SYSH_PRIORITY_DEFAULT]`
- `[chip.h:NVIC_SYSH_PRIORITY_MAX]`
- `[irq.h:STM32_IRQ_RESERVED]`
- `[irq.h:STM32_IRQ_NMI]`
- `[irq.h:STM32_IRQ_HARDFAULT]`
- `[irq.h:STM32_IRQ_MEMFAULT]`
- `[irq.h:STM32_IRQ_BUSFAULT]`
- `[irq.h:STM32_IRQ_USAGEFAULT]`
- `[irq.h:STM32_IRQ_SVCALL]`
- `[irq.h:STM32_IRQ_DBGMONITOR]`
- `[irq.h:STM32_IRQ_PENDSV]`
- `[irq.h:STM32_IRQ_SYSTICK]`
- `[irq.h:STM32_IRQ_FIRST]`
- `[stm32n6xx_irq.h:STM32_IRQ_PVD_PVM]`
- `[stm32n6xx_irq.h:STM32_IRQ_DTS]`
- `[stm32n6xx_irq.h:STM32_IRQ_RCC]`
- `[stm32n6xx_irq.h:STM32_IRQ_LOCKUP]`
- `[stm32n6xx_irq.h:STM32_IRQ_CACHE_ECC]`
- `[stm32n6xx_irq.h:STM32_IRQ_TCM_ECC]`
- `[stm32n6xx_irq.h:STM32_IRQ_BKP_ECC]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
