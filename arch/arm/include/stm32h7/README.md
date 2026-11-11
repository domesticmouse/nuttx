# stm32h7 (`nuttx/arch/arm/include/stm32h7`)

## Overview
Hardware abstraction and architecture package for `stm32h7` under `nuttx/arch/arm/include/stm32h7`, providing 7 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`, `stm32h7rsxx_irq.h`, `stm32h7x3xx_irq.h`).

## Interface
- `[chip.h:STM32_SRAM_SIZE]`
- `[chip.h:STM32_SRAM1_SIZE]`
- `[chip.h:STM32_SRAM2_SIZE]`
- `[chip.h:STM32_SRAM3_SIZE]`
- `[chip.h:STM32_SRAM123_SIZE]`
- `[chip.h:STM32_SRAM4_SIZE]`
- `[chip.h:STM32_DTCM_SRAM_SIZE]`
- `[chip.h:STM32_ITCM_SRAM_SIZE]`
- `[chip.h:STM32_NGPIO]`
- `[chip.h:STM32_NDMA]`
- `[chip.h:STM32_NADC]`
- `[chip.h:STM32_NDAC]`
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
- `[stm32h7rsxx_irq.h:STM32_IRQ_PVDPVM]`
- `[stm32h7rsxx_irq.h:STM32_IRQ_RESERVED1]`
- `[stm32h7rsxx_irq.h:STM32_IRQ_DTS]`
- `[stm32h7rsxx_irq.h:STM32_IRQ_IWDG]`
- `[stm32h7rsxx_irq.h:STM32_IRQ_WWDG]`
- `[stm32h7rsxx_irq.h:STM32_IRQ_RCC]`
- `[stm32h7rsxx_irq.h:STM32_IRQ_RESERVED6]`

## Invariants
- `[chip.h:#error]` Compile-time guard: STM32 H7 chip not identified
- `[irq.h:#error]` Compile-time guard: Unsupported STM32 H7 chip

## Side Effects
- None

## Verification
- Run: `make test`
