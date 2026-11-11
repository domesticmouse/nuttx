# stm32wl5 (`nuttx/arch/arm/include/stm32wl5`)

## Overview
Hardware abstraction and architecture package for `stm32wl5` under `nuttx/arch/arm/include/stm32wl5`, providing 3 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`, `stm32wl5xxx_cpu1_irq.h`).

## Interface
- `[chip.h:STM32_SRAM1_SIZE]`
- `[chip.h:STM32_SRAM2_SIZE]`
- `[chip.h:STM32_NATIM]`
- `[chip.h:STM32_NGTIM32]`
- `[chip.h:STM32_NGTIM16]`
- `[chip.h:STM32_NBTIM]`
- `[chip.h:STM32_NLPTIM]`
- `[chip.h:STM32_NRNG]`
- `[chip.h:STM32_NUSART]`
- `[chip.h:STM32_NLPUART]`
- `[chip.h:STM32_NSPI]`
- `[chip.h:STM32_NI2C]`
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
- `[stm32wl5xxx_cpu1_irq.h:STM32_IRQ_WWDG]`
- `[stm32wl5xxx_cpu1_irq.h:STM32_IRQ_PVD]`
- `[stm32wl5xxx_cpu1_irq.h:STM32_IRQ_PVM]`
- `[stm32wl5xxx_cpu1_irq.h:STM32_IRQ_TAMPER]`
- `[stm32wl5xxx_cpu1_irq.h:STM32_IRQ_LSE_CSS]`
- `[stm32wl5xxx_cpu1_irq.h:STM32_IRQ_RTC_STAMP]`
- `[stm32wl5xxx_cpu1_irq.h:STM32_IRQ_RTC_SSRU]`

## Invariants
- `[chip.h:#error]` Compile-time guard: Unsupported STM32L5 chip
- `[irq.h:#error]` Compile-time guard: Unsupported STM32 L5 chip

## Side Effects
- None

## Verification
- Run: `make test`
