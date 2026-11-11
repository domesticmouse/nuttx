# stm32u5 (`nuttx/arch/arm/include/stm32u5`)

## Overview
Hardware abstraction and architecture package for `stm32u5` under `nuttx/arch/arm/include/stm32u5`, providing 4 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`, `stm32_irq.h`, `stm32u5xx_irq.h`).

## Interface
- `[chip.h:STM32_SRAM1_SIZE]`
- `[chip.h:STM32_SRAM2_SIZE]`
- `[chip.h:STM32_SRAM3_SIZE]`
- `[chip.h:STM32_SRAM5_SIZE]`
- `[chip.h:STM32_PRIMARY_SRAM_SIZE]`
- `[chip.h:STM32_NFSMC]`
- `[chip.h:STM32_NATIM]`
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
- `[stm32u5xx_irq.h:STM32_IRQ_WWDG]`
- `[stm32u5xx_irq.h:STM32_IRQ_PVD_PVM]`
- `[stm32u5xx_irq.h:STM32_IRQ_RTC]`
- `[stm32u5xx_irq.h:STM32_IRQ_RTC_S]`
- `[stm32u5xx_irq.h:STM32_IRQ_TAMP]`
- `[stm32u5xx_irq.h:STM32_IRQ_RAMCFG]`
- `[stm32u5xx_irq.h:STM32_IRQ_FLASH]`
- `[stm32u5xx_irq.h:STM32_IRQ_FLASH_S]`
- `[stm32u5xx_irq.h:STM32_IRQ_GTZC]`
- `[stm32u5xx_irq.h:STM32_IRQ_RCC]`
- `[stm32u5xx_irq.h:STM32_IRQ_RCC_S]`

## Invariants
- `[chip.h:#error]` Compile-time guard: Unsupported STM32U5 chip
- `[irq.h:#error]` Compile-time guard: Unsupported STM32U5 chip
- `[stm32u5xx_irq.h:#error]` Compile-time guard: Unsupported STM32U5 chip

## Side Effects
- None

## Verification
- Run: `make test`
