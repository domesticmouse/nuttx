# stm32wb (`nuttx/arch/arm/include/stm32wb`)

## Overview
Hardware abstraction and architecture package for `stm32wb` under `nuttx/arch/arm/include/stm32wb`, providing 3 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`, `stm32wb_irq.h`).

## Interface
- `[chip.h:STM32_NFSMC]`
- `[chip.h:STM32_NBTIM]`
- `[chip.h:STM32_NATIM]`
- `[chip.h:STM32_NGTIM32]`
- `[chip.h:STM32_NLPTIM]`
- `[chip.h:STM32_NGTIMNDMA]`
- `[chip.h:STM32_NGTIM16]`
- `[chip.h:STM32_NGTIM]`
- `[chip.h:STM32_NDMA]`
- `[chip.h:STM32_NI2S]`
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
- `[stm32wb_irq.h:STM32_IRQ_WWDG]`
- `[stm32wb_irq.h:STM32_IRQ_PVD]`
- `[stm32wb_irq.h:STM32_IRQ_PVM1]`
- `[stm32wb_irq.h:STM32_IRQ_PVM3]`
- `[stm32wb_irq.h:STM32_IRQ_TAMPER]`
- `[stm32wb_irq.h:STM32_IRQ_TIMESTAMP]`
- `[stm32wb_irq.h:STM32_IRQ_LSECSS]`
- `[stm32wb_irq.h:STM32_IRQ_RTC_WKUP]`

## Invariants
- `[chip.h:#error]` Compile-time guard: Unsupported STM32WB chip

## Side Effects
- None

## Verification
- Run: `make test`
