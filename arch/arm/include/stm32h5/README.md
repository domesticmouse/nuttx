# stm32h5 (`nuttx/arch/arm/include/stm32h5`)

## Overview
Hardware abstraction and architecture package for `stm32h5` under `nuttx/arch/arm/include/stm32h5`, providing 3 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`, `stm32h5xx_irq.h`).

## Interface
- `[chip.h:STM32_SRAM1_SIZE]`
- `[chip.h:STM32_SRAM2_SIZE]`
- `[chip.h:STM32_SRAM3_SIZE]`
- `[chip.h:STM32_NRNG]`
- `[chip.h:STM32_NFSMC]`
- `[chip.h:STM32_NATIM]`
- `[irq.h:STM32_IRQ_RESERVED]`
- `[irq.h:STM32_IRQ_NMI]`
- `[irq.h:STM32_IRQ_HARDFAULT]`
- `[irq.h:STM32_IRQ_MEMFAULT]`
- `[irq.h:STM32_IRQ_BUSFAULT]`
- `[irq.h:STM32_IRQ_USAGEFAULT]`
- `[irq.h:STM32_IRQ_SECUREFAULT]`
- `[irq.h:STM32_IRQ_SVCALL]`
- `[irq.h:STM32_IRQ_DBGMONITOR]`
- `[irq.h:STM32_IRQ_PENDSV]`
- `[irq.h:STM32_IRQ_SYSTICK]`
- `[irq.h:STM32_IRQ_FIRST]`
- `[stm32h5xx_irq.h:STM32_IRQ_WWDG]`
- `[stm32h5xx_irq.h:STM32_IRQ_PVD_AVD]`
- `[stm32h5xx_irq.h:STM32_IRQ_RTC]`
- `[stm32h5xx_irq.h:STM32_IRQ_RTC_S]`
- `[stm32h5xx_irq.h:STM32_IRQ_TAMP]`
- `[stm32h5xx_irq.h:STM32_IRQ_RAMCFG]`
- `[stm32h5xx_irq.h:STM32_IRQ_FLASH]`
- `[stm32h5xx_irq.h:STM32_IRQ_FLASH_S]`
- `[stm32h5xx_irq.h:STM32_IRQ_GTZC]`
- `[stm32h5xx_irq.h:STM32_IRQ_RCC]`
- `[stm32h5xx_irq.h:STM32_IRQ_RCC_S]`
- `[stm32h5xx_irq.h:STM32_IRQ_EXTI0]`

## Invariants
- `[chip.h:#error]` Compile-time guard: Unsupported STM32H5 chip
- `[irq.h:#error]` Compile-time guard: Unsupported STM32 H5 chip

## Side Effects
- None

## Verification
- Run: `make test`
