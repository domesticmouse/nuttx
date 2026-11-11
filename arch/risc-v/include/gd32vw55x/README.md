# gd32vw55x (`nuttx/arch/risc-v/include/gd32vw55x`)

## Overview
Hardware abstraction and architecture package for `gd32vw55x` under `nuttx/arch/risc-v/include/gd32vw55x`, providing 2 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`).

## Interface
- `[chip.h:GD32VW55X_FLASH_SIZE]`
- `[chip.h:GD32VW55X_NGPIO]`
- `[chip.h:GD32VW55X_SRAM_SIZE]`
- `[chip.h:GD32VW55X_APP_SRAM_SIZE]`
- `[irq.h:GD32VW55X_IRQ_SFT]`
- `[irq.h:GD32VW55X_IRQ_TMR]`
- `[irq.h:GD32VW55X_IRQ_WWDGT]`
- `[irq.h:GD32VW55X_IRQ_LVD]`
- `[irq.h:GD32VW55X_IRQ_TAMPER_STAMP]`
- `[irq.h:GD32VW55X_IRQ_RTC_WKUP]`
- `[irq.h:GD32VW55X_IRQ_FMC]`
- `[irq.h:GD32VW55X_IRQ_RCU]`
- `[irq.h:GD32VW55X_IRQ_EXTI0]`
- `[irq.h:GD32VW55X_IRQ_EXTI1]`
- `[irq.h:GD32VW55X_IRQ_EXTI2]`
- `[irq.h:GD32VW55X_IRQ_EXTI3]`

## Invariants
- `[chip.h:#error]` Compile-time guard: Unknown GD32VW55x chip variant

## Side Effects
- None

## Verification
- Run: `make test`
