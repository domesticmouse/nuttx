# n32h7 (`nuttx/arch/arm/include/n32h7`)

## Overview
Hardware abstraction and architecture package for `n32h7` under `nuttx/arch/arm/include/n32h7`, providing 3 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`, `n32h76x_irq.h`).

## Interface
- `[chip.h:N32H7_AXI_RAM_SIZE]`
- `[chip.h:N32H7_AHB_RAM_SIZE]`
- `[chip.h:N32H7_DTCM_SRAM_SIZE]`
- `[chip.h:N32H7_ITCM_SRAM_SIZE]`
- `[chip.h:N32H7_NGPIO]`
- `[chip.h:N32H7_NDMA]`
- `[chip.h:N32H7_NADC]`
- `[irq.h:N32_IRQ_RESERVED]`
- `[irq.h:N32_IRQ_NMI]`
- `[irq.h:N32_IRQ_HARDFAULT]`
- `[irq.h:N32_IRQ_MEMFAULT]`
- `[irq.h:N32_IRQ_BUSFAULT]`
- `[irq.h:N32_IRQ_USAGEFAULT]`
- `[irq.h:N32_IRQ_SVCALL]`
- `[irq.h:N32_IRQ_DBGMONITOR]`
- `[irq.h:N32_IRQ_PENDSV]`
- `[irq.h:N32_IRQ_SYSTICK]`
- `[irq.h:N32_IRQ_FIRST]`
- `[n32h76x_irq.h:N32_IRQ_WWDG1]`
- `[n32h76x_irq.h:N32_IRQ_PVD]`
- `[n32h76x_irq.h:N32_IRQ_RTC_TAMPER]`
- `[n32h76x_irq.h:N32_IRQ_RTC_WKUP]`
- `[n32h76x_irq.h:N32_IRQ_RCC]`
- `[n32h76x_irq.h:N32_IRQ_EXTI0]`
- `[n32h76x_irq.h:N32_IRQ_EXTI1]`
- `[n32h76x_irq.h:N32_IRQ_EXTI2]`
- `[n32h76x_irq.h:N32_IRQ_EXTI3]`
- `[n32h76x_irq.h:N32_IRQ_EXTI4]`
- `[n32h76x_irq.h:N32_IRQ_EXTI9_5]`
- `[n32h76x_irq.h:N32_IRQ_EXTI15_10]`

## Invariants
- `[chip.h:#error]` Compile-time guard: CONFIG_N32H7_IO_CONFIG_x Not Set
- `[irq.h:#error]` Compile-time guard: N32 H7 chip not identified

## Side Effects
- None

## Verification
- Run: `make test`
