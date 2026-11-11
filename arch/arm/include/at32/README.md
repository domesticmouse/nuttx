# at32 (`nuttx/arch/arm/include/at32`)

## Overview
Hardware abstraction and architecture package for `at32` under `nuttx/arch/arm/include/at32`, providing 3 header file(s) and 0 source file(s) (including `at32f43xxx_irq.h`, `chip.h`, `irq.h`).

## Interface
- `[at32f43xxx_irq.h:AT32_IRQ_WWDG]`
- `[at32f43xxx_irq.h:AT32_IRQ_PVD]`
- `[at32f43xxx_irq.h:AT32_IRQ_TAMPER]`
- `[at32f43xxx_irq.h:AT32_IRQ_TIMESTAMP]`
- `[at32f43xxx_irq.h:AT32_IRQ_RTC_WKUP]`
- `[at32f43xxx_irq.h:AT32_IRQ_FLASH]`
- `[at32f43xxx_irq.h:AT32_IRQ_RCC]`
- `[at32f43xxx_irq.h:AT32_IRQ_EXTI0]`
- `[at32f43xxx_irq.h:AT32_IRQ_EXTI1]`
- `[at32f43xxx_irq.h:AT32_IRQ_EXTI2]`
- `[at32f43xxx_irq.h:AT32_IRQ_EXTI3]`
- `[at32f43xxx_irq.h:AT32_IRQ_EXTI4]`
- `[chip.h:__HAVE_F4]`
- `[chip.h:__HAVE_LD]`
- `[chip.h:__HAVE_MD]`
- `[chip.h:__HAVE_MPD]`
- `[chip.h:__HAVE_HD]`
- `[chip.h:AT32_NFSMC]`
- `[chip.h:AT32_NATIM]`
- `[irq.h:AT32_IRQ_RESERVED]`
- `[irq.h:AT32_IRQ_NMI]`
- `[irq.h:AT32_IRQ_HARDFAULT]`
- `[irq.h:AT32_IRQ_MEMFAULT]`
- `[irq.h:AT32_IRQ_BUSFAULT]`
- `[irq.h:AT32_IRQ_USAGEFAULT]`
- `[irq.h:AT32_IRQ_SVCALL]`
- `[irq.h:AT32_IRQ_DBGMONITOR]`
- `[irq.h:AT32_IRQ_PENDSV]`
- `[irq.h:AT32_IRQ_SYSTICK]`
- `[irq.h:AT32_IRQ_FIRST]`

## Invariants
- `[chip.h:#error]` Compile-time guard: Only one AT32 family must be selected !
- `[irq.h:#error]` Compile-time guard: Unsupported AT32 chip

## Side Effects
- None

## Verification
- Run: `make test`
