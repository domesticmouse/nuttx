# stm32l5 (`nuttx/arch/arm/include/stm32l5`)

## Overview
Hardware abstraction and architecture package for `stm32l5` under `nuttx/arch/arm/include/stm32l5`, providing 4 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`, `stm32l562xx_irq.h`, `stm32l5_irq.h`).

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
- `[stm32l562xx_irq.h:STM32_IRQ_WWDG]`
- `[stm32l562xx_irq.h:STM32_IRQ_PVD_PVM]`
- `[stm32l562xx_irq.h:STM32_IRQ_RTC]`
- `[stm32l562xx_irq.h:STM32_IRQ_RTC_S]`
- `[stm32l562xx_irq.h:STM32_IRQ_TAMP]`
- `[stm32l562xx_irq.h:STM32_IRQ_TAMP_S]`
- `[stm32l562xx_irq.h:STM32_IRQ_FLASH]`
- `[stm32l562xx_irq.h:STM32_IRQ_FLASH_S]`
- `[stm32l562xx_irq.h:STM32_IRQ_GTZC]`
- `[stm32l562xx_irq.h:STM32_IRQ_RCC]`
- `[stm32l562xx_irq.h:STM32_IRQ_RCC_S]`
- `[stm32l562xx_irq.h:STM32_IRQ_EXTI0]`
- `[stm32l5_irq.h:STM32_IRQ_RESERVED]`
- `[stm32l5_irq.h:STM32_IRQ_NMI]`
- `[stm32l5_irq.h:STM32_IRQ_HARDFAULT]`
- `[stm32l5_irq.h:STM32_IRQ_MEMFAULT]`
- `[stm32l5_irq.h:STM32_IRQ_BUSFAULT]`
- `[stm32l5_irq.h:STM32_IRQ_USAGEFAULT]`

## Invariants
- `[chip.h:#error]` Compile-time guard: Unsupported STM32L5 chip
- `[irq.h:#error]` Compile-time guard: Unsupported STM32 L5 chip
- `[stm32l562xx_irq.h:#error]` Compile-time guard: Unsupported STM32L5 chip

## Side Effects
- None

## Verification
- Run: `make test`
