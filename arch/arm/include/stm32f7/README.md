# stm32f7 (`nuttx/arch/arm/include/stm32f7`)

## Overview
Hardware abstraction and architecture package for `stm32f7` under `nuttx/arch/arm/include/stm32f7`, providing 5 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`, `stm32f72xx73xx_irq.h`, `stm32f74xx75xx_irq.h`).

## Interface
- `[chip.h:STM32_SRAM1_SIZE]`
- `[chip.h:STM32_SRAM2_SIZE]`
- `[chip.h:STM32_DTCM_SRAM_SIZE]`
- `[chip.h:STM32_ITCM_SRAM_SIZE]`
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
- `[stm32f72xx73xx_irq.h:STM32_IRQ_WWDG]`
- `[stm32f72xx73xx_irq.h:STM32_IRQ_PVD]`
- `[stm32f72xx73xx_irq.h:STM32_IRQ_TAMPER]`
- `[stm32f72xx73xx_irq.h:STM32_IRQ_TIMESTAMP]`
- `[stm32f72xx73xx_irq.h:STM32_IRQ_RTC_WKUP]`
- `[stm32f72xx73xx_irq.h:STM32_IRQ_FLASH]`
- `[stm32f72xx73xx_irq.h:STM32_IRQ_RCC]`
- `[stm32f72xx73xx_irq.h:STM32_IRQ_EXTI0]`
- `[stm32f72xx73xx_irq.h:STM32_IRQ_EXTI1]`
- `[stm32f72xx73xx_irq.h:STM32_IRQ_EXTI2]`
- `[stm32f72xx73xx_irq.h:STM32_IRQ_EXTI3]`
- `[stm32f72xx73xx_irq.h:STM32_IRQ_EXTI4]`
- `[stm32f74xx75xx_irq.h:STM32_IRQ_WWDG]`
- `[stm32f74xx75xx_irq.h:STM32_IRQ_PVD]`
- `[stm32f74xx75xx_irq.h:STM32_IRQ_TAMPER]`

## Invariants
- `[chip.h:#error]` Compile-time guard: STM32 F7 chip not identified
- `[irq.h:#error]` Compile-time guard: Unsupported STM32 F7 chip

## Side Effects
- None

## Verification
- Run: `make test`
