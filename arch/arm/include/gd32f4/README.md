# gd32f4 (`nuttx/arch/arm/include/gd32f4`)

## Overview
Hardware abstraction and architecture package for `gd32f4` under `nuttx/arch/arm/include/gd32f4`, providing 3 header file(s) and 0 source file(s) (including `chip.h`, `gd32f4xx_irq.h`, `irq.h`).

## Interface
- `[chip.h:GD32_NGPIO_PORTS]`
- `[chip.h:GD32_NCRC]`
- `[chip.h:GD32_NTRNG]`
- `[chip.h:GD32_NDMA]`
- `[chip.h:GD32_NIPA]`
- `[chip.h:GD32_NIREF]`
- `[chip.h:GD32_NADC]`
- `[chip.h:GD32_NDAC]`
- `[chip.h:GD32_NATIMER]`
- `[chip.h:GD32_NGTIMER]`
- `[chip.h:GD32_NGTIMNDMA]`
- `[chip.h:GD32_NBTIMER]`
- `[gd32f4xx_irq.h:GD32_IRQ_WWDGT]`
- `[gd32f4xx_irq.h:GD32_IRQ_LVD]`
- `[gd32f4xx_irq.h:GD32_IRQ_TAMPER_STAMP]`
- `[gd32f4xx_irq.h:GD32_IRQ_RTC_WKUP]`
- `[gd32f4xx_irq.h:GD32_IRQ_FMC]`
- `[gd32f4xx_irq.h:GD32_IRQ_RCU_CTC]`
- `[gd32f4xx_irq.h:GD32_IRQ_EXTI0]`
- `[gd32f4xx_irq.h:GD32_IRQ_EXTI1]`
- `[gd32f4xx_irq.h:GD32_IRQ_EXTI2]`
- `[gd32f4xx_irq.h:GD32_IRQ_EXTI3]`
- `[gd32f4xx_irq.h:GD32_IRQ_EXTI4]`
- `[gd32f4xx_irq.h:GD32_IRQ_DMA0_CHANNEL0]`
- `[irq.h:GD32_IRQ_RESERVED]`
- `[irq.h:GD32_IRQ_NMI]`
- `[irq.h:GD32_IRQ_HARDFAULT]`
- `[irq.h:GD32_IRQ_MEMFAULT]`
- `[irq.h:GD32_IRQ_BUSFAULT]`
- `[irq.h:GD32_IRQ_USAGEFAULT]`

## Invariants
- `[chip.h:#error]` Compile-time guard: Unknown GD32F4 chip type
- `[gd32f4xx_irq.h:#error]` Compile-time guard: Unknown GD32F4xx chip.
- `[irq.h:#error]` Compile-time guard: Unknown GD32 chip

## Side Effects
- None

## Verification
- Run: `make test`
