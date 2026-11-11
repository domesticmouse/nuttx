# stm32c5 (`nuttx/arch/arm/include/stm32c5`)

## Overview
Hardware abstraction and architecture package for `stm32c5` under `nuttx/arch/arm/include/stm32c5`, providing 3 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`, `stm32_irq.h`).

## Interface
- `[chip.h:STM32_SRAM1_SIZE]`
- `[chip.h:STM32_SRAM2_SIZE]`
- `[chip.h:STM32_PRIMARY_SRAM_SIZE]`
- `[chip.h:STM32_NFSMC]`
- `[chip.h:STM32_NATIM]`
- `[chip.h:STM32_NGTIM32]`
- `[chip.h:STM32_NGTIM16]`
- `[chip.h:STM32_NGTIMNDMA]`
- `[chip.h:STM32_NBTIM]`
- `[chip.h:STM32_NLPTIM]`
- `[chip.h:STM32_NRNG]`
- `[chip.h:STM32_NUART]`
- `[stm32_irq.h:STM32_IRQ_RESERVED]`
- `[stm32_irq.h:STM32_IRQ_NMI]`
- `[stm32_irq.h:STM32_IRQ_HARDFAULT]`
- `[stm32_irq.h:STM32_IRQ_MEMFAULT]`
- `[stm32_irq.h:STM32_IRQ_BUSFAULT]`
- `[stm32_irq.h:STM32_IRQ_USAGEFAULT]`
- `[stm32_irq.h:STM32_IRQ_SECUREFAULT]`
- `[stm32_irq.h:STM32_IRQ_SVCALL]`
- `[stm32_irq.h:STM32_IRQ_DBGMONITOR]`
- `[stm32_irq.h:STM32_IRQ_PENDSV]`
- `[stm32_irq.h:STM32_IRQ_SYSTICK]`
- `[stm32_irq.h:STM32_IRQ_FIRST]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
