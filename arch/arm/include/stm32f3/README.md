# stm32f3 (`nuttx/arch/arm/include/stm32f3`)

## Overview
Hardware abstraction and architecture package for `stm32f3` under `nuttx/arch/arm/include/stm32f3`, providing 5 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`, `stm32f30xxx_irq.h`, `stm32f33xxx_irq.h`).

## Interface
- `[chip.h:STM32_NFSMC]`
- `[chip.h:STM32_NATIM]`
- `[chip.h:STM32_NGTIM]`
- `[chip.h:STM32_NGTIMNDMA]`
- `[chip.h:STM32_NBTIM]`
- `[chip.h:STM32_NDMA]`
- `[chip.h:STM32_NSPI]`
- `[chip.h:STM32_NI2S]`
- `[chip.h:STM32_NUSART]`
- `[chip.h:STM32_NLPUART]`
- `[chip.h:STM32_NI2C]`
- `[chip.h:STM32_NCAN]`
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
- `[stm32f30xxx_irq.h:STM32_IRQ_WWDG]`
- `[stm32f30xxx_irq.h:STM32_IRQ_PVD]`
- `[stm32f30xxx_irq.h:STM32_IRQ_TAMPER]`
- `[stm32f30xxx_irq.h:STM32_IRQ_TIMESTAMP]`
- `[stm32f30xxx_irq.h:STM32_IRQ_RTC_WKUP]`
- `[stm32f30xxx_irq.h:STM32_IRQ_FLASH]`
- `[stm32f30xxx_irq.h:STM32_IRQ_RCC]`

## Invariants
- `[chip.h:#error]` Compile-time guard: Unsupported STM32 chip
- `[irq.h:#error]` Compile-time guard: Unsupported STM32F3 chip

## Side Effects
- None

## Verification
- Run: `make test`
