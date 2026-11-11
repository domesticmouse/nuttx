# atmega (`nuttx/arch/avr/include/atmega`)

## Overview
Hardware abstraction and architecture package for `atmega` under `nuttx/arch/avr/include/atmega`, providing 1 header file(s) and 0 source file(s) (including `irq.h`).

## Interface
- `[irq.h:ATMEGA_IRQ_INT0]`
- `[irq.h:ATMEGA_IRQ_INT1]`
- `[irq.h:ATMEGA_IRQ_INT2]`
- `[irq.h:ATMEGA_IRQ_INT3]`
- `[irq.h:ATMEGA_IRQ_INT4]`
- `[irq.h:ATMEGA_IRQ_INT5]`
- `[irq.h:ATMEGA_IRQ_INT6]`
- `[irq.h:ATMEGA_IRQ_INT7]`
- `[irq.h:ATMEGA_IRQ_T2COMP]`
- `[irq.h:ATMEGA_IRQ_T2OVF]`
- `[irq.h:ATMEGA_IRQ_T1CAPT]`
- `[irq.h:ATMEGA_IRQ_T1COMPA]`

## Invariants
- `[irq.h:#error]` Compile-time guard: CONFIG_AVR_HAS_RAMPZ is supposed to be set for this chip

## Side Effects
- None

## Verification
- Run: `make test`
