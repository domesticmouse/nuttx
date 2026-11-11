# avrdx (`nuttx/arch/avr/include/avrdx`)

## Overview
Hardware abstraction and architecture package for `avrdx` under `nuttx/arch/avr/include/avrdx`, providing 1 header file(s) and 0 source file(s) (including `irq.h`).

## Interface
- `[irq.h:AVRDX_IRQ_NMI]`
- `[irq.h:AVRDX_IRQ_BOD_VLM]`
- `[irq.h:AVRDX_IRQ_RTC_CNT]`
- `[irq.h:AVRDX_IRQ_RTC_PIT]`
- `[irq.h:AVRDX_IRQ_CCL_CCL]`
- `[irq.h:AVRDX_IRQ_PORTA_PORT]`
- `[irq.h:AVRDX_IRQ_TCA0_LUNF]`
- `[irq.h:AVRDX_IRQ_TCA0_OVF]`
- `[irq.h:AVRDX_IRQ_TCA0_HUNF]`
- `[irq.h:AVRDX_IRQ_TCA0_CMP0]`
- `[irq.h:AVRDX_IRQ_TCA0_LCMP0]`
- `[irq.h:AVRDX_IRQ_TCA0_CMP1]`

## Invariants
- `[irq.h:#error]` Compile-time guard: CONFIG_AVR_HAS_RAMPZ is supposed to be set for this chip

## Side Effects
- None

## Verification
- Run: `make test`
