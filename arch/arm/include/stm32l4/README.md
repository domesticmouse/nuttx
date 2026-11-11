# stm32l4 (`nuttx/arch/arm/include/stm32l4`)

## Overview
Hardware abstraction and architecture package for `stm32l4` under `nuttx/arch/arm/include/stm32l4`, providing 6 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`, `stm32l4x3xx_irq.h`, `stm32l4x5xx_irq.h`).

## Interface
- `[chip.h:STM32_SRAM1_SIZE]`
- `[chip.h:STM32_SRAM2_SIZE]`
- `[chip.h:STM32_SRAM3_SIZE]`
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
- `[stm32l4x3xx_irq.h:STM32_IRQ_WWDG]`
- `[stm32l4x3xx_irq.h:STM32_IRQ_PVD]`
- `[stm32l4x3xx_irq.h:STM32_IRQ_TAMPER]`
- `[stm32l4x3xx_irq.h:STM32_IRQ_TIMESTAMP]`
- `[stm32l4x3xx_irq.h:STM32_IRQ_RTC_WKUP]`
- `[stm32l4x3xx_irq.h:STM32_IRQ_FLASH]`
- `[stm32l4x3xx_irq.h:STM32_IRQ_RCC]`
- `[stm32l4x3xx_irq.h:STM32_IRQ_EXTI0]`
- `[stm32l4x3xx_irq.h:STM32_IRQ_EXTI1]`
- `[stm32l4x3xx_irq.h:STM32_IRQ_EXTI2]`
- `[stm32l4x3xx_irq.h:STM32_IRQ_EXTI3]`
- `[stm32l4x3xx_irq.h:STM32_IRQ_EXTI4]`
- `[stm32l4x5xx_irq.h:STM32_IRQ_WWDG]`
- `[stm32l4x5xx_irq.h:STM32_IRQ_PVD]`
- `[stm32l4x5xx_irq.h:STM32_IRQ_TAMPER]`
- `[stm32l4x5xx_irq.h:STM32_IRQ_TIMESTAMP]`

## Invariants
- `[chip.h:#error]` Compile-time guard: Unsupported STM32L4 chip
- `[irq.h:#error]` Compile-time guard: Unsupported STM32 L4 chip
- `[stm32l4x3xx_irq.h:#error]` Compile-time guard: Unsupported STM32L4 chip
- `[stm32l4x6xx_irq.h:#error]` Compile-time guard: Unsupported STM32L4 chip

## Side Effects
- None

## Verification
- Run: `make test`
