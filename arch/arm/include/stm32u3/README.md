# stm32u3 (`nuttx/arch/arm/include/stm32u3`)

## Overview
Hardware abstraction and architecture package for `stm32u3` under `nuttx/arch/arm/include/stm32u3`, providing 4 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`, `stm32_irq.h`, `stm32u3c5xx_irq.h`).

## Interface
- `[chip.h:STM32_SRAM1_SIZE]`
- `[chip.h:STM32_SRAM2_SIZE]`
- `[chip.h:STM32_SRAM3_SIZE]`
- `[chip.h:STM32_SRAM4_SIZE]`
- `[chip.h:STM32_PRIMARY_SRAM_SIZE]`
- `[chip.h:STM32_NFSMC]`
- `[chip.h:STM32_NATIM]`
- `[chip.h:STM32_NGTIM32]`
- `[chip.h:STM32_NGTIM16]`
- `[chip.h:STM32_NGTIMNDMA]`
- `[chip.h:STM32_NBTIM]`
- `[chip.h:STM32_NLPTIM]`
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
- `[stm32u3c5xx_irq.h:STM32_IRQ_WWDG]`
- `[stm32u3c5xx_irq.h:STM32_IRQ_PVD_PVM]`
- `[stm32u3c5xx_irq.h:STM32_IRQ_RTC]`
- `[stm32u3c5xx_irq.h:STM32_IRQ_RTC_S]`
- `[stm32u3c5xx_irq.h:STM32_IRQ_TAMP]`
- `[stm32u3c5xx_irq.h:STM32_IRQ_RAMCFG]`

## Invariants
- `[chip.h:#error]` Compile-time guard: Unsupported STM32U3 chip
- `[irq.h:#error]` Compile-time guard: Unsupported STM32U3 chip

## Side Effects
- None

## Verification
- Run: `make test`
